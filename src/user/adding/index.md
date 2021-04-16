# Adding Glean to your project

This page describes the steps for adding Glean to a project. This does not include the
steps for adding a new metrics or pings to an existing Glean integration. If that is what
your are looking for, refer to the [Adding new metrics]() or the [Adding new pings]() guide.

## Glean integration checklist

The Glean integration checklist can help to ensure your Glean-using product
is meeting all of the recommended guidelines.

Products using Glean to collect telemetry **must**:

- Integrate Glean into their build system.
  - Glean requires code generation for your metrics and pings, thus integrating Glean into your
    build system is a bit more complex than simply importing the Glean library.
- Request [data review]() for including Glean in their project.
  - Glean itself collects [internal metrics]() and sends [internal pings](), therefore it is
    required that you go through a data review just for adding Glean to your project.
- Ensure that telemetry coming from automated testing or continuous integration is either not sent
  to the telemetry server or [tagged with the `automation` tag using the `sourceTag` feature]().
- [File a data engineering bug]() to enable their product's application id.

{{#include ../../../assets/info.html}}

### Looking for an integration guide?

> Step-by-step integration guides for each supported language/environment,
> can be found on the specific integration guides:
>
> - [Kotlin](./kotlin.md)
> - [Swift](./swift.md)
> - [Python](./python.md)
> - [Rust](./rust.md)
> - [Javascript](./javascript.md)
> - [Firefox Desktop](./firefox.md)


