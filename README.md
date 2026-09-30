# USB Memory Manager --- By NORTH

A simple Windows utility for managing backups of USB flash drives and
external USB drives through an interactive terminal-style interface.

## Features

USB Memory Manager provides the following options:

``` text
[1] Restore a previous backup
[2] Create a backup of the drive
[3] Completely erase the drive (DESTRUCTIVE)
[4] Open backup folder
[0] Exit
```

### Restore a previous backup

Restores a previously created backup to the selected USB flash drive or
external drive.

The restore operation copies the backup files to the destination without
automatically deleting unrelated files that are already present on the
drive.

### Create a backup of the drive

Creates a backup of the selected USB/external drive on the computer.

Backups are stored in:

``` text
Documents\USB Memory Manager\Backups
```

The program uses Windows **Robocopy** to copy the files and generates a
log of the operation.

### Completely erase the drive

Permanently erases the selected physical USB drive using Windows
**DiskPart `CLEAN ALL`**.

Before the erase begins, the application displays information about the
selected device, including its:

-   Drive letter
-   Volume label
-   Capacity
-   Physical disk number
-   Device model

Two explicit confirmations are required before the erase command is
executed.

> \[!CAUTION\] This operation is destructive and cannot be undone.
> Always verify the drive model, capacity, drive letter, and physical
> disk number before confirming.

`CLEAN ALL` writes zeros to accessible sectors. On SSDs and flash
storage, controller-level wear leveling and remapped cells mean
overwrite-based erasure cannot guarantee physical erasure of every
memory cell. When available, a manufacturer's Secure Erase or Sanitize
function is preferable for that purpose.

### Open backup folder

Opens the folder containing backups created by USB Memory Manager.

## Automatic USB detection

The application scans Windows storage devices and detects volumes that
are either removable or connected through a USB bus.

If multiple compatible drives are connected, the program lets you select
the device you want to use.

## Logs

Operation logs are stored in:

``` text
Documents\USB Memory Manager\Logs
```

These logs can help identify files copied by Robocopy or errors
encountered during backup and restore operations.

## Requirements

-   Windows 10 or Windows 11
-   USB flash drive or external USB storage device

## How to use

Download the latest release and launch:

``` text
USB Memory Manager - By NORTH.exe
```

Connect your USB flash drive or external drive, then select the desired
operation from the main menu.

## Backup structure

Backups are saved locally and separated using the USB device information
and backup date.

Example:

``` text
Documents/
└── USB Memory Manager/
    ├── Backups/
    │   ├── USB_DRIVE_E_2026-09-30_18-45-00/
    │   └── USB_DRIVE_E_2026-10-01_12-30-00/
    └── Logs/
```

Each backup also contains metadata describing the original device.

## Safety

The application intentionally requires additional confirmation for
destructive operations.

Nevertheless, always verify the selected device before performing an
erase. Do not disconnect a drive while an erase, backup, or restore
operation is in progress.

For important data, maintain more than one independent backup.

## Author

Developed by **NORTH**.

## Disclaimer

This software is provided as a drive backup and management utility. Test
backup and restore operations with non-critical data before relying on
the application for important files.

The author is not responsible for data loss, accidental disk selection,
hardware failure, interrupted operations, or misuse of the software.
