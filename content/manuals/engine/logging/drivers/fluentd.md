---
description: Learn how to use the fluentd logging driver
keywords: Fluentd, docker, logging, driver
title: Fluentd logging driver
aliases:
  - /engine/reference/logging/fluentd/
  - /reference/logging/fluentd/
  - /engine/admin/logging/fluentd/
  - /config/containers/logging/fluentd/
---

The `fluentd` logging driver sends container logs to the
[Fluentd](https://www.fluentd.org) collector as structured log data. Then, users
can use any of the [various output plugins of
Fluentd](https://www.fluentd.org/plugins) to write these logs to various
destinations.

In addition to the log message itself, the `fluentd` log
driver sends the following metadata in the structured log message:

| Field            | Description                                                                                                                                           |
| :--------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------- |
| `container_id`   | The full 64-character container ID.                                                                                                                   |
| `container_name` | The container name at the time it was started. If you use `docker rename` to rename a container, the new name isn't reflected in the journal entries. |
| `source`         | `stdout` or `stderr`                                                                                                                                  |
| `log`            | The container log                                                                                                                                     |

## Usage

Some options are supported by specifying `--log-opt` as many times as needed:

- `fluentd-address`: specify a socket address to connect to the Fluentd daemon, ex `fluentdhost:24224` or `unix:///path/to/fluentd.sock`.
- `tag`: specify a tag for Fluentd messages. Supports some Go template markup, ex `{{.ID}}`, `{{.FullID}}` or `{{.Name}}` `docker.{{.ID}}`.

To use the `fluentd` driver as the default logging driver, set the `log-driver`
and `log-opt` keys to appropriate values in the `daemon.json` file, which is
located in `/etc/docker/` on Linux hosts or
`C:\ProgramData\docker\config\daemon.json` on Windows Server. For more about
configuring Docker using `daemon.json`, see [daemon.json](/reference/cli/dockerd.md#daemon-configuration-file).

The following example sets the log driver to `fluentd` and sets the
`fluentd-address` option.

```json
{
  "log-driver": "fluentd",
  "log-opts": {
    "fluentd-address": "fluentdhost:24224"
  }
}
```

Restart Docker for the changes to take effect.

> [!NOTE]
>
> `log-opts` configuration options in the `daemon.json` configuration file must
> be provided as strings. Boolean and numeric values (such as the value for
> `fluentd-async` or `fluentd-max-retries`) must therefore be enclosed
> in quotes (`"`).

To set the logging driver for a specific container, pass the
`--log-driver` option to `docker run`:

```console
$ docker run --log-driver=fluentd ...
```

Before using this logging driver, launch a Fluentd daemon. The logging driver
connects to this daemon through `localhost:24224` by default. Use the
`fluentd-address` option to connect to a different address.

```console
$ docker run --log-driver=fluentd --log-opt fluentd-address=fluentdhost:24224
```

If container cannot connect to the Fluentd daemon, the container stops
immediately unless the `fluentd-async` option is used.

## Options

Users can use the `--log-opt NAME=VALUE` flag to specify additional Fluentd logging driver options.

### fluentd-address

By default, the logging driver connects to `localhost:24224`. Supply the
`fluentd-address` option to connect to a different address. `tcp`(default) and `unix` sockets are supported.

```console
$ docker run --log-driver=fluentd --log-opt fluentd-address=fluentdhost:24224
$ docker run --log-driver=fluentd --log-opt fluentd-address=tcp://fluentdhost:24224
$ docker run --log-driver=fluentd --log-opt fluentd-address=unix:///path/to/fluentd.sock
```

Two of the above specify the same address, because `tcp` is default.

### tag

By default, Docker uses the first 12 characters of the container ID to tag log messages.
Refer to the [log tag option documentation](log_tags.md) for customizing
the log tag format.

### labels, labels-regex, env, and env-regex

The `labels` and `env` options each take a comma-separated list of keys. If
there is collision between `label` and `env` keys, the value of the `env` takes
precedence. Both options add additional fields to the extra attributes of a
logging message.

The `env-regex` and `labels-regex` options are similar to and compatible with
respectively `env` and `labels`. Their values are regular expressions to match
logging-related environment variables and labels. It is used for advanced
[log tag options](log_tags.md).

### fluentd-async

Docker connects to Fluentd in the background. Messages are buffered until the
connection is established. Defaults to `false`.

### fluentd-async-reconnect-interval

When `fluentd-async` is enabled, the `fluentd-async-reconnect-interval` option
defines the interval, in milliseconds, at which the connection to
`fluentd-address` is re-established. This option is useful if the address
resolves to one or more IP addresses, for example a Consul service address.

### fluentd-buffer-limit

Sets the number of events buffered on the memory. Records will be stored in memory
up to this number. If the buffer is full, the call to record logs will fail.
The default is 1048576.
(https://github.com/fluent/fluent-logger-golang/tree/master#bufferlimit)

### fluentd-retry-wait

How long to wait between retries. Defaults to 1 second.

### fluentd-max-retries

The maximum number of retries. Defaults to `4294967295` (2\*\*32 - 1).

### fluentd-sub-second-precision

Generates event logs in nanosecond resolution. Defaults to `false`.

### fluentd-write-timeout

Sets the timeout for the write call to the `fluentd` daemon. By default,
writes have no timeout and will block indefinitely.

## Fluentd daemon management with Docker

About `Fluentd` itself, see [the project webpage](https://www.fluentd.org)
and [its documents](https://docs.fluentd.org).

To use this logging driver, start the `fluentd` daemon on a host. We recommend
that you use [the Fluentd docker
image](https://hub.docker.com/r/fluent/fluentd/). This image is
especially useful if you want to aggregate multiple container logs on each
host then, later, transfer the logs to another Fluentd node to create an
aggregate store.

### Test container loggers

1.  Write a configuration file (`test.conf`) to dump input logs:

    ```text
    <source>
      @type forward
    </source>

    <match *>
      @type stdout
    </match>
    ```

2.  Launch Fluentd container with this configuration file:

    ```console
    $ docker run -it -p 24224:24224 -v /path/to/conf/test.conf:/fluentd/etc/test.conf -e FLUENTD_CONF=test.conf fluent/fluentd:latest
    ```

3.  Start one or more containers with the `fluentd` logging driver:

    ```console
    $ docker run --log-driver=fluentd your/application
    ```
