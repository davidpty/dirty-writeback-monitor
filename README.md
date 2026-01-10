# Dirty Writeback Monitor

A lightweight **terminal-based Linux monitoring tool** for observing **dirty memory, writeback activity and I/O pressure** in real time.

The tool is designed for **system engineers, performance analysts and advanced Linux users** who need visibility into how memory-backed writes are flushed to disk and how this affects overall system behavior.

---

## What This Tool Monitors

### Dirty Memory

Memory pages that have been modified in RAM but **not yet written to disk**.

High dirty memory can indicate:

* Write-heavy workloads
* Delayed disk I/O
* Potential latency spikes during forced writeback

### Writeback

Pages actively being flushed from memory to disk.

Sustained writeback can indicate:

* Disk saturation
* Storage bottlenecks
* I/O contention with applications

### PSI (Pressure Stall Information)

Linux kernel metrics that show **how often tasks are stalled** waiting for I/O.

This helps correlate memory pressure with real system impact.

---

## Key Features

* Real-time terminal UI
* Tracks dirty pages and writeback volume
* Displays I/O pressure (PSI)
* Optional per-process disk write tracking
* No background daemon
* No network access

---

## Supported Platforms

* Linux only
* Kernel with PSI support (5.0+ recommended)
* `/proc` and `/sys` interfaces available

---

## Requirements

* Python 3.9+
* Linux kernel with writeback statistics enabled

Optional:

* Root privileges for per-process write attribution

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## Installation

Clone the repository:

```bash
git clone https://github.com/davidpty/dirty-writeback-monitor.git
cd dirty-writeback-monitor
```

Run directly:

```bash
python dirtymon
```

---

## Usage

Basic monitoring:

```bash
python dirtymon
```

Run with elevated privileges for per-process I/O:

```bash
sudo python dirtymon
```

Exit with `Ctrl+C`.

---

## Example Output

```
Dirty:      842 MB
Writeback:  117 MB
IO PSI:     avg10=0.21% avg60=0.08% avg300=0.01%
Top writers:
  postgres    42 MB/s
  rsync       18 MB/s
```

---

## Interpreting the Data

* **Rising dirty memory + low writeback** → disk not flushing yet
* **High writeback + high PSI** → storage bottleneck
* **Low dirty + high PSI** → I/O contention elsewhere

Use this tool alongside `iostat`, `vmstat`, or `perf` for deeper analysis.

---

## Use Cases

* Diagnosing disk latency spikes
* Understanding memory writeback behavior
* Tuning dirty ratio and writeback kernel parameters
* Observing impact of heavy write workloads

---

## Security & Privacy

* All data is read locally from the kernel
* No files are written
* No network access

---

## Project Status

* Actively maintained
* Interface considered stable for CLI usage
* No background services or persistent state

---

## Contributing

Contributions are welcome if they:

* Keep runtime overhead minimal
* Avoid background processes
* Preserve terminal-first usability

Open an issue before large changes.

---

## License

MIT
