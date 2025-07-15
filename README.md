# ubuntu-wsl-build

Ansible Playbook to automatically configure Ubuntu VMs for WSL (to my preferences). Will install new tools, and configure OS settings.

Heavily inspired by [Ippsec](https://github.com/ippsec/parrot-build/) and his video series using Ansible for ParrotOS on [Youtube](https://youtube.com/playlist?list=PLidcsTyj9JXJVIFqyHBHzrRYKPpZYFjM8&si=6n2xfM20y4F5v_i1)

## Installation
### 1. Install Ubuntu for WSL

#### Method #1: Microsoft Store
https://apps.microsoft.com/detail/9pdxgncfsczv?hl=en-US&gl=US

#### Method #2: Image Import
* Download image https://ubuntu.com/desktop/wsl
* Import image with WSL:
```
wsl --install --from-file "<.wsl_file>" --location "<install_location>" --name "<instance_name>"
```

### 2. Install ansible
```bash
sudo apt install ansible
```

### 3. Clone this repository and go into it
```bash
git clone https://github.com/treywb/ubuntu-wsl-build

cd ubuntu-wsl-build/
```

### 5. Run the playbook & provide user password when prompted
```bash
ansible-playbook main.yml --ask-become-pass
```

If you encounter the error:

`ERROR: Ansible could not initialize the preferred locale: unsupported locale setting`

This command will set the required environment variable:
`export LC_ALL="C.UTF-8"`

## Post-Installation
- System reboot required for some changes to take effect
- Manually finish installation of BloodHound-CE, Tmux plugins, & FoxyProxy

### 1. Reboot system

**System reboot required for some changes to take effect**
```powershell
wsl --shutdown
```

### 2. Initialize Tmux Theme
- Launch tmux in terminal: `tmux new`
- Finalize plugin installation: `<Ctrl B> + <i>`

### 3. Initialize gh auth
```bash
gh auth setup-git

gh auth login
```