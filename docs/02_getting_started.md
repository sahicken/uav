# Getting Started

## Software

### Project Docs

[Markdown](https://www.markdownguide.org/basic-syntax/) is the file format of choice for UAV Project Docs because it's easy-to-learn and well-supported on Github. Please use `pandoc docs/*.md -o README.md` before submitting a pull request if it modifies any files in `docs/`. Links to high-quality resources are located throughout this document, including begineer resources such as [the Github basics](https://docs.github.com/en/get-started). **Please use the links!**

### Dependencies

Most Linux distros running a desktop environment should work, however [Fedora](https://docs.fedoraproject.org/en-US/fedora/latest/getting-started/) or [Ubuntu](https://ubuntu.com/tutorials/install-ubuntu-desktop) will be assumed. On Windows installing virtualization software such as [VMware](https://en.wikipedia.org/wiki/VMware_Workstation_Player) or [Virtualbox](https://en.wikipedia.org/wiki/VirtualBox) is necessary. **WSL2 does not yet work with these instructions!** 12GB RAM or more is highly recommended for virtualization. To reduce RAM requirements consider installing either Lubuntu or Xubuntu.

After installing a supported distro, install docker using [these instructions for Fedora](https://docs.docker.com/engine/install/fedora/) or [the Ubuntu instructions here](https://docs.docker.com/engine/install/ubuntu/). On Fedora you **must** run `sudo systemctl start docker` after every reboot or instead just [configure docker to start upon boot](https://docs.docker.com/engine/install/linux-postinstall/#configure-docker-to-start-on-boot-with-systemd). This is unnecessary for Ubuntu.

### note about sections

All sections should be limited to their most simple components in the getting started section

## Design

No design section in getting started yet.

## Electronics

No electronics section either.
