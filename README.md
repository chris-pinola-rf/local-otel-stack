# Local OpenTelemetry Tracing Stack

## Getting Started

1. Clone this repo.
1. Bring up the local dev stack with `docker compose up` from inside this directory.
1. Download the [OpenTelemetry javaagent JAR](https://github.com/open-telemetry/opentelemetry-java-instrumentation/releases/download/v1.10.0/opentelemetry-javaagent.jar) and move it somewhere where it can be read by your app at runtime.
1. Start your JVM app with the following environment variables defined:
    1. `JAVA_TOOL_OPTIONS=-javaagent:/path/to/javaagent/jar/from/prior/step/opentelemetry-javaagent.jar`
    1. `OTEL_EXPORTER_OTLP_ENDPOINT=http://localhost:4317`
    1. `OTEL_SERVICE_NAME=name_of_your_app`
    1. `OTEL_RESOURCE_ATTRIBUTES=deployment.environment=local`
1. Explore your traces via the Jaeger UI on http://localhost:16686/

Note: depending on your platform you may need to use `host.docker.internal` instead of `localhost` to access the local Jaeger and OTel Collector instances.