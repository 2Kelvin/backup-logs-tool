# Linux Log & Data Backup Tool

A lightweight, reliable Bash utility designed to automate the compression and archival of system logs and data directories. Built for Linux administrators, this tool ensures that backups are structured, timestamped, and logged for easy auditing across any distribution.

## 🚀 Features

* **Smart Compression:** Uses `tar` with Gzip compression to minimize storage footprint.
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

## 🛠 Installation

To run this tool from anywhere, it should be installed in `/usr/local/bin`. This directory is intended for executable programs installed locally by the system administrator.

1.  **Move the script to the local bin:**
    ```bash
    sudo mv backup_script.sh /usr/local/bin/logbackup
    ```

2.  **Apply executable permissions:**
    ```bash
    sudo chmod +x /usr/local/bin/logbackup
    ```

3.  **Verify it's in your PATH:**
    ```bash
    which logbackup
    ```

---

## 📖 Usage

Because this tool writes to system-protected directories, it must be run with **root** privileges or via **sudo**.

### Basic Syntax
```bash
sudo logbackup <folder_path>