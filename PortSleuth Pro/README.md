<div align="center">

# 🔍 PortSleuth Pro

### Advanced Multi-Threaded Network Port Scanner with Professional Report Generation

[![Python](https://img.shields.io/badge/Python-3.8%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-22c55e?style=for-the-badge)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux%20%7C%20macOS-64748b?style=for-the-badge)](#)
[![Purpose](https://img.shields.io/badge/Purpose-Authorized%20Security%20Testing-f59e0b?style=for-the-badge)](#-security--ethical-use)
<img width="1410" height="1078" alt="image" src="https://github.com/user-attachments/assets/9c1f5783-0e32-4e8a-be74-11d78b77968a" />


<br/>

> A Python-based network reconnaissance tool designed for authorized security testing, network administration, and cybersecurity education.

</div>

---

## 📋 Table of Contents

- [Features](#-features)
- [Installation](#-installation)
- [Usage](#-usage)
- [Report Formats](#-report-formats)
- [Project Structure](#-project-structure)
- [Dependencies](#-dependencies)
- [Testing the Tool](#-testing-the-tool)
- [Example Output](#-example-output)
- [Security & Ethical Use](#-security--ethical-use)
- [Future Improvements](#-future-improvements)
- [License](#-license)

---

## ✨ Features

| Feature | Description |
|---|---|
| ⚡ **Multi-Threaded Scanning** | Parallel threads dramatically reduce scan time across large port ranges |
| 🔎 **Service Detection** | Automatically identifies common services (SSH, HTTP, FTP, SMTP, MySQL, etc.) |
| 🏷️ **Banner Grabbing** | Retrieves service banners to fingerprint web servers, mail servers, SSH versions |
| 🚨 **Risk Assessment** | Classifies each open port as HIGH / MEDIUM / LOW risk |
| 📊 **Multi-Format Reports** | Generates professional reports in TXT, JSON, CSV, HTML, and PDF |
| 🖥️ **Clean CLI Interface** | Full control over port range, threads, timeout, and output format |
| 📁 **Organized Output** | All reports auto-saved to `reports/` with timestamps |

### Risk Classification

| Level | Color | Description |
|---|---|---|
| 🔴 HIGH | Red | Potentially dangerous exposed services |
| 🟡 MEDIUM | Yellow | Common services requiring active monitoring |
| 🟢 LOW | Green | Low-risk open ports |

---

## ⚙️ Installation

### Prerequisites

- Python **3.8** or higher
- `pip` package manager
- Network access to the target (with proper authorization)

### Step 1 — Clone the Repository

```bash
git clone https://github.com/yourusername/PortSleuth-Pro.git
cd PortSleuth-Pro
```

### Step 2 — Create a Virtual Environment (Recommended)

```bash
python -m venv venv
```

Activate it:

**Windows:**
```bash
venv\Scripts\activate
```

**Linux / macOS:**
```bash
source venv/bin/activate
```

### Step 3 — Install Dependencies

```bash
pip install -r requirements.txt
```

---

## 🚀 Usage

### Basic Scan

Scan the default common ports on a target:

```bash
python -m src.core_scanner scanme.nmap.org
```

### Scan a Specific Port Range

```bash
python -m src.core_scanner scanme.nmap.org -s 20 -e 1000
```

### Advanced Scan with All Options

```bash
python -m src.core_scanner scanme.nmap.org -s 1 -e 2000 -t 200 -T 0.5 --report html
```

### CLI Options Reference

| Flag | Long Form | Default | Description |
|---|---|---|---|
| `-s` | `--start` | `1` | Start port number |
| `-e` | `--end` | `1024` | End port number |
| `-t` | `--threads` | `100` | Number of parallel threads |
| `-T` | `--timeout` | `1.0` | Connection timeout (seconds) |
| `--report` | — | `txt` | Report format: `txt` `json` `csv` `html` `pdf` `all` |

---

## 📄 Report Formats

PortSleuth Pro can generate reports in five formats. All reports are saved to the `reports/` directory with a timestamp in the filename.

```bash
# Generate HTML report
python -m src.core_scanner scanme.nmap.org --report html

# Generate PDF report
python -m src.core_scanner scanme.nmap.org --report pdf

# Generate all formats at once
python -m src.core_scanner scanme.nmap.org --report all
```

**Example output filename:**
```
reports/scan_45_33_32_156_20260313_164520.html
```

Each report includes target information, scan timestamp, duration, port results, service identification, risk classification, and captured service banners.

---

## 📁 Project Structure

```
PortSleuth-Pro/
│
├── README.md                   ← You are here
├── LICENSE                     ← MIT License
├── requirements.txt            ← Python dependencies
├── setup.py                    ← Package setup
├── .gitignore
│
├── src/
│   ├── __init__.py
│   ├── core_scanner.py         ← Main scanning engine & CLI
│   ├── report_generator.py     ← Multi-format report generation
│   └── utils.py                ← Helpers & service definitions
│
├── tests/
│   └── test_basic.py           ← Unit tests
│
├── examples/
│   └── example_scan.py         ← Usage examples
│
├── docs/
│   └── usage.md                ← Extended documentation
│
└── reports/                    ← Auto-generated scan reports
```

---

## 📦 Dependencies

| Library | Version | Purpose |
|---|---|---|
| `colorama` | ≥0.4.6 | Colored terminal output |
| `reportlab` | ≥4.0.0 | PDF report generation |
| `jinja2` | ≥3.1.0 | HTML report templating |
| `tqdm` | ≥4.65.0 | Progress bars |
| `tabulate` | ≥0.9.0 | Table formatting in reports |

Install all at once:
```bash
pip install -r requirements.txt
```

---

## 🧪 Testing the Tool

You can safely test PortSleuth Pro on these **authorized** targets:

**Localhost (no internet required):**
```bash
python -m src.core_scanner 127.0.0.1
```

**Nmap's public test server** *(designed specifically for security tool testing)*:
```bash
python -m src.core_scanner scanme.nmap.org
```

**Run unit tests:**
```bash
python -m pytest tests/ -v
```

---

## 📟 Example Output

**Terminal:**
```
╔══════════════════════════════════════════╗
║         PORTSLEUTH PRO  v1.0             ║
╚══════════════════════════════════════════╝

  TARGET     : scanme.nmap.org
  PORT RANGE : 1 - 1024
  THREADS    : 100
  TIMEOUT    : 1.0s

  [OPEN]  Port  22  →  ssh      [MEDIUM]
  [OPEN]  Port  80  →  http     [MEDIUM]

  ────────────────────────────────────────
  SCAN COMPLETE
  Duration      : 2.4 seconds
  Open Ports    : 2
  Report saved  : reports/scan_45_33_32_156_20260313.html
```

**TXT Report:**
```
PORTSLEUTH PRO - NETWORK PORT SCAN REPORT
==========================================

Target   : scanme.nmap.org
Date     : 2026-03-13
Duration : 2.41 seconds

PORT    SERVICE    RISK      BANNER
──────────────────────────────────────────
22      SSH        MEDIUM    OpenSSH 6.6.1
80      HTTP       MEDIUM    Apache/2.4.7
```

---

## ⚠️ Security & Ethical Use

**PortSleuth Pro is intended strictly for authorized security testing and educational purposes.**

✅ **Permitted use:**
- Scanning your own systems and networks
- Scanning systems you have explicit written permission to test
- Authorized penetration testing engagements
- Educational use in controlled lab environments

❌ **Prohibited use:**
- Scanning systems without explicit authorization
- Scanning random public hosts or websites
- Any use that violates local laws or regulations

> Unauthorized port scanning may be illegal in your jurisdiction. The author assumes no liability for misuse of this tool. Always obtain **explicit written permission** before scanning any system you do not own.

---

## 🔮 Future Improvements

- [ ] UDP port scanning support
- [ ] Nmap integration for advanced fingerprinting
- [ ] OS detection
- [ ] Network host discovery
- [ ] Vulnerability correlation with CVE database
- [ ] Interactive HTML dashboard with charts
- [ ] GUI interface (Tkinter / PyQt)
- [ ] Docker deployment support
- [ ] Scheduled / automated scanning
- [ ] Slack / email alerting for report delivery

---

## 👨‍💻 Author

Developed by **AJ**

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

⭐ **If you found PortSleuth Pro useful, please consider starring the repository!**

</div>
