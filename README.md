# rpi-ubuntu-server-kernel-decompress-service
Ubuntu Server on Raspberry Pi cannot boot from compressed kernel on external USB drive; solution: a service that monitors for kernel updates and auto-decompresses


## Installation

On target Raspberry Pi system booted from external USB drive, complete the following:

1. Copy `decompress-kernel` to `/usr/local/bin/`
2. Copy `decompress-kernel.service` and `decompress-kernel.path` to `/etc/systemd/system/`
3. `sudo systemctl start decompress-kernel.path`
4. `sudo systemctl enable decompress-kernel.path`
5. Confirm working by touching expected file: `touch /var/run/reboot-required`
6. Check that `decompress-kernel` executes successfully by inspecting log: `sudo journalctl -u decompress-kernel.service`