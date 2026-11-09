# Gamma Top 0.1.0

**Gamma Aurora · GTK 3 · Native Linux telemetry**

Gamma Top is a graphical system monitor for Gamma Linux and Debian-based systems. It reads Linux `/proc` and `/sys` directly; it does not depend on `psutil`, `top`, `htop`, or a background daemon.

## Current implementation

- Overview: CPU utilisation, RAM, swap, uptime, load average and process count.
- Processes: PID, command, user, CPU sample, resident memory, state and parent PID; search and explicit SIGTERM/SIGKILL confirmation.
- Performance: short rolling CPU and memory graphs drawn with Cairo.
- Network: per-interface RX/TX counters and sampled rates.
- Storage: mounted filesystem usage plus block-device counters and sampled rates.
- Hardware: thermal-zone temperatures and CPU frequency when exposed by the kernel.
- Collector: standard-library Python readers for procfs/sysfs; UI refresh is scheduled through GLib.

Telemetry that the kernel or device does not expose is shown as unavailable rather than fabricated. The first sample of rate-based metrics is a baseline, so rates settle after the next refresh. Process CPU is calculated from process ticks against aggregate CPU ticks and is approximate across multi-core systems.

## Runtime dependencies

On Debian/Gamma Linux:

```sh
sudo apt install python3 python3-gi gir1.2-gtk-3.0 python3-cairo
```

Run from the source tree:

```sh
PYTHONPATH=. python3 -m gamma_top
```

Build the simple Debian package:

```sh
./packaging/build-deb.sh
sudo apt install ./dist/gamma-top_0.1.0_all.deb
```

The package script uses `dpkg-deb`; it does not need network access.

## Architecture

- `gamma_top/core/procfs.py`: pure Python procfs/sysfs collector and parsers.
- `gamma_top/ui/`: GTK 3 interface and Cairo history graphs.
- `tests/`: parser and CPU-delta unit tests.

Collectors are kept separate from GTK widgets so they can be tested without a display server. The current UI is a first working foundation; later versions can add per-process CPU history, temperature labels, sorting refinements and more complete device metadata.

## Safety

Gamma Top runs without root for monitoring. Process signals are explicit user actions and require a confirmation dialog. SIGKILL is intentionally available only as a manual action. No telemetry is uploaded and no network connection is created.

## License

GPL-3.0-or-later. See `LICENSE`.
