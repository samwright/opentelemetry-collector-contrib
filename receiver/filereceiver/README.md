# File Receiver

<!-- status autogenerated section -->
| Status        |           |
| ------------- |-----------|
| Stability     | [development]: metrics, traces, logs   |
| Distributions | [contrib] |
| Issues        | ![Open issues](https://img.shields.io/github/issues-search/open-telemetry/opentelemetry-collector-contrib?query=is%3Aissue%20is%3Aopen%20label%3Areceiver%2Ffile%20&label=open&color=orange&logo=opentelemetry) ![Closed issues](https://img.shields.io/github/issues-search/open-telemetry/opentelemetry-collector-contrib?query=is%3Aissue%20is%3Aclosed%20label%3Areceiver%2Ffile%20&label=closed&color=blue&logo=opentelemetry) |

[development]: https://github.com/open-telemetry/opentelemetry-collector#development
[contrib]: https://github.com/open-telemetry/opentelemetry-collector-releases/tree/main/distributions/otelcol-contrib
<!-- end autogenerated section -->

The File Receiver reads the output of a
[File Exporter](https://github.com/open-telemetry/opentelemetry-collector-contrib/tree/main/exporter/fileexporter),
converting that output to metrics, and sending the metrics down the pipeline.

Currently, the only file format supported is the File Exporter's JSON format. Reading compressed output, rotated files,
or telemetry other than metrics are not supported at this time.

## Getting Started

The following setting is required:

- `path` [no default]: the file in the same format as written by a File Exporter.

The following setting is optional:

- `throttle` [default: 1]: a determines how fast telemetry is replayed. A value of `0` means
  that it will be replayed as fast as the system will allow. A value of `1` means that it will
  be replayed at the same rate as the data came in, as indicated by the timestamps on the
  input file's telemetry data. Higher values mean that the replay speed will be slower by a
  multiple of the throttle value. Values can be decimals, e.g. `0.5` means that telemetry will be
  replayed at 2x the rate indicated by the telemetry's timestamps.

## Example

```yaml
receivers:
  file:
    path: my-telemetry-file
    throttle: 0.5
```
