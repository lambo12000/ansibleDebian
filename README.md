# Ansible Debian Setup Playbook

This Ansible playbook automates the setup of a basic Debian environment on the local machine.

## Tasks Performed

The playbook executes the following tasks:

1.  **Update Apt Cache & Install Core Tools:**
    *   Updates the `apt` package cache.
    *   Installs `vim`, `nala`, and `git`.
2.  **Install Desktop Environment Components:**
    *   Installs `xserver-xorg`, `i3` (window manager), and `lightdm` (display manager).
3.  **Install Additional Utilities:**
    *   Installs `kitty` (terminal emulator) and `suckless-tools`.
4.  **Configure Shell Aliases:**
    *   Adds `alias sudo="sudo "` to `~/.bashrc`.
    *   Adds `alias apt="nala"` to `~/.bashrc`.

## How to Run

Execute the playbook from within the `ansibleDebian` directory using the following command:

```bash
ansible-playbook debian.yaml --ask-become-pass
```
