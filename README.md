# NetworkPulse: TCP Service Monitor

<div align="center">
  <p><strong>A powerful, Python-based TCP service monitoring and alerting system</strong></p>
  <p>
    <a href="#features">Features</a> •
    <a href="#overview">Overview</a> •
    <a href="#installation">Installation</a> •
    <a href="#usage">Usage</a> •
    <a href="#monitoring-capabilities">Monitoring Capabilities</a> •
    <a href="#architecture">Architecture</a> •
    <a href="#requirements">Requirements</a> •
    <a href="#contributing">Contributing</a>
  </p>
</div>

## Overview

NetworkPulse is a robust TCP service monitoring system that provides real-time monitoring and alerting capabilities. Built with Python, it enables system administrators, DevOps engineers, and IT professionals to monitor critical network services, track their availability, and receive instant notifications about service disruptions.

Whether you're managing a small network or a large infrastructure, NetworkPulse provides an efficient and reliable way to monitor service availability, track response times, and ensure system reliability through immediate alerting and a user-friendly web interface.

## Features

- **🔍 Real-time Service Monitoring**: Continuous monitoring of TCP ports and HTTP services
- **⚡ Quick Response Detection**: Accurate response time measurement for all monitored services
- **📊 Service Status Dashboard**: Clean web interface showing real-time service states
- **🔔 Instant Alerts**: Real-time notifications via Telegram when services go down
- **📈 Uptime Tracking**: Detailed uptime/downtime statistics for all services
- **🔄 HTTP(S) Validation**: Advanced HTTP response code and content verification
- **🎯 Custom Actions**: Execute scripts automatically when services fail
- **👥 Service Grouping**: Organize services into logical groups for better management
- **📱 Mobile-Friendly**: Responsive web interface accessible from any device
- **🔧 Easy Management**: Simple CLI tool for service management

## Installation

### Prerequisites

- Python 3
- pip package manager
- Apache/httpd web server
- SQLite3

### Setup Instructions

1. **Clone the Repository**
   ```bash
   git clone https://github.com/VaibhavDaveDev/NetworkPulse.git
   cd NetworkPulse
   ```

2. **Install Dependencies**
   ```bash
   pip3 install -r requirements.txt
   ```

3. **Install System Service**
   ```bash
   sudo mkdir -p /opt/NetworkPulse
   sudo cp networkpulse.py networkpulsectl.py sql.py networkpulse.cfg /opt/NetworkPulse/
   sudo chmod +x /opt/NetworkPulse/*.py
   sudo ./sql.py
   sudo cp networkpulse.service /etc/systemd/system/
   sudo systemctl daemon-reload
   sudo systemctl enable networkpulse
   sudo systemctl start networkpulse
   sudo ln -s /opt/NetworkPulse/networkpulsectl.py /usr/local/bin/networkpulsectl
   ```

4. **Setup Web Interface**
   ```bash
   sudo cp www/networkpulse.conf /etc/httpd/conf.d/
   sudo cp -r www/networkpulse /var/www/
   sudo systemctl reload httpd
   ```

## Usage

### Command Line Interface

```bash
# Add a new service to monitor
networkpulsectl add <ip> <port> [options]

# List all monitored services
networkpulsectl list

# Enable/Disable monitoring
networkpulsectl enable <ip> <port>
networkpulsectl disable <ip> <port>

# Edit service configuration
networkpulsectl edit <ip> <port> [options]

# Delete a service
networkpulsectl del <ip> <port>
```

### Configuration Options

- **--desc**: Add service description
- **--group**: Assign to a service group
- **--http**: Set HTTP endpoint for validation
- **--body**: Specify required content in HTTP response
- **--script**: Set failure response script

## Monitoring Capabilities

### TCP Service Monitoring
- Port availability checking
- Response time measurement
- Connection state tracking

### HTTP(S) Service Validation
- Status code verification
- Response content validation
- SSL/TLS support

### Alert System
- Telegram notifications
- Custom script execution
- Immediate failure detection

## Architecture

NetworkPulse follows a modular architecture with these key components:

- **Core Monitor (networkpulse.py)**: Main service monitoring engine
- **Control Interface (networkpulsectl.py)**: Command-line management tool
- **Database Handler (sql.py)**: SQLite database management
- **Web Interface**: Real-time monitoring dashboard

### Key Components

- **Monitor Engine**: Handles service checks and alerts
- **Database**: Stores configurations and states
- **Web Dashboard**: Provides visual monitoring interface
- **Alert System**: Manages notification delivery

## Requirements

### System Requirements
- **OS**: Linux (Debian/RHEL based)
- **Python**: 3 or higher
- **RAM**: 256 MB minimum
- **Storage**: 100 MB
- **Network**: Active internet connection

### Additional Requirements
- Apache/httpd web server
- SQLite3 database
- Python pip package manager

## Contributing

We welcome contributions! Here's how you can help:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<div align="center">
  <p>
    <a href="https://github.com/VaibhavDaveDev/NetworkPulse/stargazers">⭐ Star this repo</a> •
    <a href="https://github.com/VaibhavDaveDev/NetworkPulse/issues/new">🐛 Report bug</a> •
    <a href="https://github.com/VaibhavDaveDev/NetworkPulse/issues/new">✨ Request feature</a>
  </p>
  <p>
    © 2025 <a href="https://github.com/VaibhavDaveDev">Vaibhav Dave</a>
  </p>
</div>
