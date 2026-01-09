# Dirty Writeback Monitor

A simple, real-time terminal monitor for Linux Dirty Memory and Writeback activity, built with [Rich](https://github.com/Textualize/rich).

It helps you understand system I/O pressure by visualizing:
- **Dirty & Writeback Memory usage**
- **Drain speed (writeback rate)**
- **System Pressure Information (PSI) for I/O and Memory**
- **Top processes currently writing to disk**

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/dirty-writeback-monitor.git
   cd dirty-writeback-monitor
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

Run the script with Python 3:

```bash
./dirtymon
# or
python3 dirtymon
```

> **Note:** Accessing `/proc/` files for other processes (to calculate per-process write rates) might require root privileges to see full details, or simply running as a regular user will suffice for global stats and owned processes.

## License

MIT
