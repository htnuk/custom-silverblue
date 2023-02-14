# Custom Silverblue Image

This is a customised Fedora Silverblue image based on the work by [uBlue](https://ublue.it/).

## Usage

Warning: This is an experimental feature, be wary about using it in production.

```bash
sudo rpm-ostree rebase --experimental ostree-unverified-registry:ghcr.io/htnuk/custom-silverblue:latest
```

## Features

- Removes Firefox from the base image
- Adds the following packages to the base image:
  - Arm Image Installer
  - Distrobox
  - ZSH
- Sets automatic staging of updates for the system
- Sets Flatpaks to update twice a day

## Applications

- Core GNOME Applications are replaced with Flathub equivalents:
  - GNOME Calculator
  - Calendar
  - Characters
  - Connections
  - Contacts
  - Evince
  - Firmware
  - Logs
  - Maps
  - Nautilus Previewer
  - Text Editor
  - Weather
  - Baobab
  - Clocks
  - EOG
  - Font Viewer

- The following additional applications are installed:
  - Bitwarden
  - Cockpit Client
  - Cryptomator
  - DejaDup
  - Extension Manager
  - Flatseal
  - GIMP
  - Libreoffice
  - Mozilla Firefox
  - Mozilla Thunderbird
  - PeaZip
  - Protonmail Bridge
  - Remmina
  - Ungoogled Chromium
  - VLC Media Player
  - Whalebird Desktop
  - WhatsApp Desktop

## Further Customization

The `just` task runner is included for further customization after first boot.
It will copy the template from `/etc/justfile` to your home directory.
After that run the following commands:

- `just` - Show all tasks, more will be added in the future
- `just bios` - Reboot into the system bios (Useful for dualbooting)
- `just changelogs` - Show the changelogs of the pending update
- Set up distroboxes for the following images:
  - `just distrobox-appbox`
  - `just distrobox-fedbox`
- `just setup-gaming` - Install Steam, Lutris, Bottles, and ProtonUp-Qt. MangoHud is installed and enabled by default, hit right Shift-F12 to toggle
- `just update` - Update rpm-ostree, flatpaks, and distroboxes in one command

Check the [just website](https://just.systems) for tips on modifying and adding your own recipes. 
  
## Verification

These images are signed with sisgstore's [cosign](https://docs.sigstore.dev/cosign/overview/). You can verify the signature by downloading the `cosign.pub` key from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/htnuk/custom-silverblue
```
    
If you're forking this repo you should [read the docs](https://docs.github.com/en/actions/security-guides/encrypted-secrets) on keeping secrets in github. You need to [generate a new keypair](https://docs.sigstore.dev/cosign/overview/) with cosign. The public key can be in your public repo (your users need it to check the signatures), and you can paste the private key in Settings -> Secrets -> Actions.

# Making your Own

1. Visit the [uBlue-os base repository](https://github.com/ublue-os/base)
2. Click the `Use this template` button.
3. Follow the instructions in the README.md
