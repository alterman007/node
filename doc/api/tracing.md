# Tracing

<!--introduced_in=v7.7.0-->

Trace Event provides a mechanism to centralize tracing information generated by
V8, Node core, and userspace code.

Tracing can be enabled by passing the `--trace-events-enabled` flag when
starting a Node.js application.

The set of categories for which traces are recorded can be specified using the
`--trace-event-categories` flag followed by a list of comma separated category
names.

The available categories are:

* `node`
* `node.async_hooks` - Enables capture of detailed async_hooks trace data.
* `node.perf` - Enables capture of [Performance API] measurements.
  * `node.perf.usertiming` - Enables capture of only Performance API User Timing
    measures and marks.
  * `node.perf.timerify` - Enables capture of only Performance API timerify
    measurements.
* `v8`

By default the `node`, `node.async_hooks`, and `v8` categories are enabled.

```txt
node --trace-events-enabled --trace-event-categories v8,node,node.async_hooks server.js
```

Running Node.js with tracing enabled will produce log files that can be opened
in the [`chrome://tracing`](https://www.chromium.org/developers/how-tos/trace-event-profiling-tool)
tab of Chrome.

Starting with Node 10.0.0, the tracing system uses the same time source as the
one used by `process.hrtime()` however the trace-event timestamps are expressed
in microseconds, unlike `process.hrtime()` which returns nanoseconds.

[Performance API]: perf_hooks.html
