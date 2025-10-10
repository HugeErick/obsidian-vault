# Linux Systemd Service Management Guide

## Table of Contents
- [Understanding Systemd Services](#understanding-systemd-services)
- [Creating a Custom Service](#creating-a-custom-service)
- [Managing Services](#managing-services)
- [Monitoring Services](#monitoring-services)
- [Removing Services](#removing-services)
- [Troubleshooting](#troubleshooting)

## Understanding Systemd Services

Systemd is the init system and service manager for most modern Linux distributions. Services are defined in `.service` files that control how and when programs run in the background.

### Key Service Directories
- `/etc/systemd/system/` - System administrator services (recommended for custom services)
- `/usr/lib/systemd/system/` - System/package installed services
- `~/.config/systemd/user/` - User-specific services (if enabled)

## Creating a Custom Service

### Step 1: Create the Service File

Create your service file in the system directory:
```bash
sudo nano /etc/systemd/system/your-service-name.service
```

### Step 2: Service File Template

Here's a comprehensive template based on your web scraper example:

```ini
[Unit]
Description=Your Service Description
Documentation=https://example.com/docs
After=network.target
Wants=network-online.target
# Requires=other-service.target  # Uncomment if your service depends on others

[Service]
Type=simple
User=your-username              # Optional: run as specific user
Group=your-group                # Optional: run as specific group
WorkingDirectory=/path/to/your/working/directory
ExecStart=/usr/bin/your-command --your-flags
ExecReload=/bin/kill -HUP $MAINPID
ExecStop=/bin/kill -TERM $MAINPID
Restart=always
RestartSec=10
StandardOutput=journal
StandardError=journal
Environment=VAR1=value1
Environment=VAR2=value2

# Security options (recommended)
NoNewPrivileges=yes
ProtectSystem=strict
ProtectHome=yes

[Install]
WantedBy=multi-user.target
```

### Step 3: Key Configuration Options Explained

#### [Unit] Section
- `Description`: Human-readable service description
- `After`: Start after these targets/services
- `Wants`: Soft dependencies
- `Requires`: Hard dependencies (service fails if these fail)

#### [Service] Section
- `Type`:
  - `simple` (default): Main process is the service itself
  - `forking`: Process forks and parent exits
  - `oneshot`: Run once and exit
  - `notify`: Service notifies when ready

- `Restart` policies:
  - `no`: Never restart
  - `always`: Always restart
  - `on-success`: Restart only on clean exit
  - `on-failure`: Restart only on failure

- `RestartSec`: Seconds to wait before restarting

#### [Install] Section
- `WantedBy`: Which target should start this service

### Step 4: Enable and Start the Service

```bash
# Reload systemd to recognize new service
sudo systemctl daemon-reload

# Enable service to start automatically at boot
sudo systemctl enable your-service-name

# Start the service immediately
sudo systemctl start your-service-name

# Check status
sudo systemctl status your-service-name
```

## Managing Services

### Basic Service Management Commands

```bash
# Start a service
sudo systemctl start service-name

# Stop a service
sudo systemctl stop service-name

# Restart a service
sudo systemctl restart service-name

# Reload service configuration (if supported)
sudo systemctl reload service-name

# Enable service to start at boot
sudo systemctl enable service-name

# Disable automatic start at boot
sudo systemctl disable service-name

# Check if service is enabled
sudo systemctl is-enabled service-name

# Reload all service files after modifications
sudo systemctl daemon-reload
```

### Viewing Service Information

```bash
# Show service status
sudo systemctl status service-name

# Show service journal logs
sudo journalctl -u service-name

# Follow logs in real-time
sudo journalctl -u service-name -f

# Show logs from specific time
sudo journalctl -u service-name --since "1 hour ago"

# Show detailed service information
sudo systemctl show service-name

# List all running services
sudo systemctl list-units --type=service

# List all available services
sudo systemctl list-unit-files --type=service
```

## Monitoring Services

### Real-time Monitoring

```bash
# Follow service logs
sudo journalctl -u service-name -f

# Show recent logs with timestamps
sudo journalctl -u service-name -n 50

# Watch service status
watch sudo systemctl status service-name

# Check service resource usage
sudo systemd-cgtop
```

### Service Health Checks

```bash
# Verify service is active
sudo systemctl is-active service-name

# Check service failed state
sudo systemctl --failed

# Test service configuration
sudo systemd-analyze verify /etc/systemd/system/service-name.service
```

## Removing Services

### Complete Service Removal Process

```bash
# Step 1: Stop the service if running
sudo systemctl stop service-name

# Step 2: Disable automatic startup
sudo systemctl disable service-name

# Step 3: Remove the service file
sudo rm /etc/systemd/system/service-name.service

# Step 4: Reload systemd
sudo systemctl daemon-reload

# Step 5: Reset failed state (if any)
sudo systemctl reset-failed

# Step 6: Verify removal
sudo systemctl list-unit-files | grep service-name
```

### One-liner Removal Script

```bash
sudo systemctl stop service-name && \
sudo systemctl disable service-name && \
sudo rm /etc/systemd/system/service-name.service && \
sudo systemctl daemon-reload && \
sudo systemctl reset-failed
```

## Troubleshooting

### Common Issues and Solutions

```bash
# Service fails to start
sudo journalctl -u service-name -n 50

# Check service dependencies
systemd-analyze critical-chain service-name

# Verify service file syntax
systemd-analyze verify /etc/systemd/system/service-name.service

# Test ExecStart command manually
sudo -u username /path/to/command --flags

# Check for permission issues
sudo journalctl -u service-name | grep -i "permission\|error\|fail"
```

### Debugging Tips

1. **Test command manually first**: Run the `ExecStart` command manually to ensure it works
2. **Check permissions**: Ensure the service user has access to required files/directories
3. **Verify paths**: Use absolute paths for all commands and working directories
4. **Check environment variables**: Use `Environment` directive or test with `printenv`
5. **Monitor logs**: Use `journalctl -u service-name -f` to watch real-time logs

### Emergency Recovery

```bash
# If service is stuck
sudo systemctl kill service-name

# Force reload systemd
sudo systemctl daemon-reexec

# Reset all service states
sudo systemctl reset-failed
```

## Example: Web Scraper Service (Your Example)

Based on your provided service file, here's how to deploy it:

```bash
# 1. Create the service file
sudo tee /etc/systemd/system/web-scraper.service > /dev/null <<EOF
[Unit]
Description=Web Scraper Service
After=network.target
Wants=network-online.target

[Service]
Type=simple
WorkingDirectory=/opt/web-scraper
ExecStart=/usr/bin/node scraper-service.mjs
Restart=always
RestartSec=10
StandardOutput=journal
StandardError=journal
Environment=NODE_ENV=production
Environment=DISPLAY=:99

[Install]
WantedBy=multi-user.target
EOF

# 2. Deploy the service
sudo systemctl daemon-reload
sudo systemctl enable web-scraper
sudo systemctl start web-scraper
sudo systemctl status web-scraper

# 3. Remove when no longer needed
sudo systemctl stop web-scraper
sudo systemctl disable web-scraper
sudo rm /etc/systemd/system/web-scraper.service
sudo systemctl daemon-reload
```
