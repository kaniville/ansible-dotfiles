# 🎩 Fedora Playbook

Fedora Workstation managed with Ansible.

![](src/screenshot.png)

## 📜 Preamble

### 🟢 What this playbook does ?

- Installs essential programs.
- hardens your Fedora Linux.
- Configure your system & programs very easily.
- Customize the Gnome environment.

### 🔴 What this playbook doesn't do ?

- Update your operating system.
- Configure any other distribution than Fedora Linux.
- Install hardware-specific programs.
- Manage your partitions or your disks.

## 🚀 Installation

> [!IMPORTANT]
> Important variables are present in the `group_vars` directory. You need to edit them to customize your installation. </br></br>
> Additional variables are also present in the `vars` directories under each roles. </br></br>
> Never run this playbook with `sudo` or as root. If you need privileges, use the `-K` argument.

Firstly, install Ansible:
```
# dnf install ansible
```

You can then clone this repository and enter it:
```
$ git clone https://github.com/steadywool/fedora-playbook.git
$ cd fedora-playbook
```

Start the playbook and configure your system with this command:
```
$ ansible-playbook playbook.yml -K
```

## ✨ Configuration

You can perform partially run of playbook using tags.

You can list them with this command:
```
$ ansible-playbook playbooks/production.yml --list-tags
```

Then use them with the `-t ROLE` parameter.

## 📕 Exemples

Install every packages & enable/start Systemd services:
```
$ ansible-playbook playbook.yml -K -t packages,services
```

Executes tasks requiring no privileges:
```
$ ansible-playbook playbook.yml -t dotfiles,desktop,services.user
```

Execute the entire playbook but skip the configuration of Usbguard & ADB:
```
$ ansible-playbook playbook.yml -K --skip-tags security.usbguard,applications.adb
```

For more arguments, check the man page with the command `man ansible-playbook`.
