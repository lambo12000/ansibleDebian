# Ansible Debian Setup Playbook

This Ansible playbook automates the setup of a basic Debian environment on the local machine.

## Tasks Performed

The playbook executes the following tasks:

1.  **Update Apt Cache & Install Core Tools:**
    *   Updates the `apt` package cache.
    *   Installs `vim`, `nala`, `git`, and `default-jre`.
2.  **Install Desktop Environment Components:**
    *   Installs `xserver-xorg`, `i3` (window manager), and `lightdm` (display manager).
3.  **Install Additional Utilities:**
    *   Installs `kitty` (terminal emulator) and `suckless-tools`.
4.  **Configure Shell Aliases:**
    *   Adds `alias sudo="sudo "` to `~/.bashrc`.
    *   Adds `alias apt="nala"` to `~/.bashrc`.
5.  **Install i3 Configuration:**
    *   Clones the `lambo12000/i3_vms` repository to a temporary location.
    *   Copies the `i3` directory from the cloned repository to `~/.config/`.
    *   Removes the temporary repository clone.

## How to Run

Execute the playbook from within the `ansibleDebian` directory using the following command:

```bash
ansible-playbook debian.yaml --ask-become-pass
