# Gamma Top

Gamma Top is the planned full graphical system monitor for Gamma Linux.

## Initial technical direction

- Python with GTK 3 and Cairo for the native desktop interface.
- Linux-native collectors based on `/proc` and `/sys`; no mandatory `psutil` dependency.
- A collector/monitoring layer separated from the GTK presentation layer.
- Dashboard, process list, performance history, network, storage, and hardware telemetry.
- Process termination actions must be explicit and confirmed by the user.

These are the agreed design choices, not a claim that the implementation is already complete.

## Workspace status

The application scaffold exists; implementation and tests are still pending.

## Planned structure

```text
Gamma-Top/
├── gamma_top/
│   ├── collectors/
│   ├── core/
│   ├── ui/
│   └── resources/
├── data/
├── debian/
├── tests/
├── README.md
└── CHANGELOG.md
```

## First milestones

- [ ] Implement and test the `/proc/stat` CPU sampler using deltas between samples.
- [ ] Implement memory, uptime, load-average, and process collectors.
- [ ] Add bounded in-memory history for charts.
- [ ] Build the GTK dashboard and process view.
- [ ] Add network, storage, and hardware pages.
- [ ] Package and test a standalone Debian `.deb`.

Do not run expensive collectors in the GTK main loop. Handle disappearing processes and PID reuse safely, and keep privileged operations separate from read-only monitoring.
