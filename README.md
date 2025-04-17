# Ansible Debian Setup Playbook

This Ansible playbook automates the setup of a basic Debian environment on the local machine.

## Tasks Performed

The playbook executes the following tasks:

1.  **Update Apt Cache & Install Core Tools:**
    *   Updates the `apt` package cache.
    *   Installs `vim`, `nala`, `git`, `ufw`, `firefox`, and `default-jre`.
2.  **Install Desktop Environment Components:**
    *   Installs `xserver-xorg`, `i3` (window manager), and `lightdm` (display manager).
3.  **Install Additional Utilities:**
    *   Installs `kitty` (terminal emulator) and `suckless-tools`.
4.  **Refresh Snap Packages (Ubuntu Only):**
    *   Runs `snap refresh` if the operating system is detected as Ubuntu.
5.  **Configure Shell Aliases:**
    *   Adds `alias sudo="sudo "` to `~/.bashrc`.
    *   Adds `alias apt="nala"` to `~/.bashrc`.
6.  **Install i3 Configuration:**
    *   Clones the `lambo12000/i3_vms` repository to a temporary location.
    *   Copies the `i3` directory from the cloned repository to `~/.config/`.
    *   Removes the temporary repository clone.
7.  **Configure UFW (Firewall):**
    *   Sets the default incoming policy to `deny`.
    *   Sets the default outgoing policy to `allow`.
    *   Enables the `ufw` firewall.
8.  **Install Ghostty (Snap):**
    *   Installs `ghostty` with snap if the operating system is detected as Ubuntu.

## Playbook Structure (Step-Based)

This repository uses a step-based approach for Ansible provisioning, ensuring dependencies are respected and each phase is clear and maintainable.

### Steps:

- **step1_base_setup.yaml**: Installs base system packages, desktop environment, and core utilities.
- **step2_user_env.yaml**: Sets up user environment, shell aliases, i3 config, and Oh My Zsh with Powerlevel10k theme.
- **step3_apps_services.yaml**: Configures UFW firewall and installs/configures Ghostty terminal.
- **site.yaml**: Master playbook that runs all steps in order.

### Usage

To run the full setup:

```sh
ansible-playbook -i invintory.ini site.yaml
```

Or run individual steps:

```sh
ansible-playbook -i invintory.ini step1_base_setup.yaml
ansible-playbook -i invintory.ini step2_user_env.yaml
ansible-playbook -i invintory.ini step3_apps_services.yaml
```

### Rationale

Splitting the playbook ensures each stage only runs after its dependencies are met, makes debugging easier, and keeps the automation robust and simple.

## Original Playbook

The previous monolithic playbook has been split for clarity and maintainability. See the new step-based files listed above.

## How to Run

Execute the playbook from within the `ansibleDebian` directory using the following command:

```bash
ansible-playbook debian.yaml --ask-become-pass
