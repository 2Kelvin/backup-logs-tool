# Linux Log & Data Backup Tool

A lightweight, reliable Bash utility designed to automate the compression and archival of system logs and data directories. Built for **Linux Sysadmins**, this tool ensures that backups are structured, timestamped, and logged for easy auditing across any distribution.

## 🚀 Features

* **Smart Compression:** Uses `tar` with **Gzip** compression to minimize storage footprint.
* **Safe Path Handling:** Automatically handles trailing slashes and relative paths using `dirname` and `basename` logic.
* **Audit Logging:** Maintains a persistent history in `/var/backups/my-logs-backup-folder/archive-logs-history.log`.
* **Error Resilience:** Automatically cleans up partial or corrupted files if the compression process is interrupted.
* **System-Wide Integration:** Designed to reside in the system `$PATH` for execution from any directory.

---

## 📂 Standardized Storage Strategy

This tool follows the **Linux Filesystem Hierarchy Standard (FHS)** by utilizing the `/var` directory:

* **Storage Path:** `/var/backups/my-logs-backup-folder/`
* **Why `/var/backups`?** Unlike `/tmp` (which is volatile) or `/home` (which is for user-specific data), `/var/backups` is the designated system area for data meant to be preserved across reboots and shared by system services.

---

## 📋 Requirements

* **OS:** Any Linux Distribution (Ubuntu, CentOS, Debian, Arch, etc.)
* **Shell:** Bash
* **Dependencies:** `tar`, `date`, `mkdir`, `du` (standard on all distros).

---

## 🛠 Installation

To run this tool from anywhere, it should be installed in `/usr/local/bin`. This directory is intended for executable programs installed locally by the system administrator.

1.  **Git clone the project:**
    ```git
    git clone https://github.com/2Kelvin/backup-logs-tool.git
    ```
    and then navigate into the directory
    ```bash
    cd backup-logs-tool
    ```

2.  **Move the script to the local bin:**
    ```bash
    sudo mv backup-tool /usr/local/bin/backup-tool
    ```

3.  **Give backup-tool executable permissions:**
    ```bash
    sudo chmod +x /usr/local/bin/backup-tool
    ```

4.  **Verify it's in your PATH:**
    ```bash
    which backup-tool
    ```

---

## 📖 Usage

Because this tool writes to and reads from system-protected directories like `/var/backups` and `/var/log`, it requires administrative privileges. You should run it as **root** or use **sudo** as a user.

### Syntax
```bash
sudo backup-tool <folder_path>
```

### Example

Add screenshot here
