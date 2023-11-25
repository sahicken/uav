# VTOL Simulation and Mission Planning

This is a [markdown](https://www.markdownguide.org/basic-syntax/) file. Markdown should be used for all the UAV project's documentation.
Links to high-quality resources are located throughout this document. **Please use them.**

## Important Dependencies

Most Linux distros running a desktop environment should work, however [Fedora](https://docs.fedoraproject.org/en-US/fedora/latest/getting-started/) or [Ubuntu](https://ubuntu.com/tutorials/install-ubuntu-desktop) will be assumed. On Windows installing virtualization software such as [VMware](https://en.wikipedia.org/wiki/VMware_Workstation_Player) or [Virtualbox](https://en.wikipedia.org/wiki/VirtualBox) is necessary. **WSL2 does not yet work with these instructions!** 12GB RAM or more is highly recommended for virtualization. To reduce RAM requirements consider installing either Lubuntu or Xubuntu.

After installing a supported distro, install docker using [these instructions for Fedora](https://docs.docker.com/engine/install/fedora/) or [the Ubuntu instructions here](https://docs.docker.com/engine/install/ubuntu/). On Fedora you **must** run `sudo systemctl start docker` after every reboot or instead just [configure docker to start upon boot](https://docs.docker.com/engine/install/linux-postinstall/#configure-docker-to-start-on-boot-with-systemd). This is unnecessary for Ubuntu.

## QGroundControl (QGC) Mission Planner

QGroundControl or simply QGC is the primary frontend for mission planning and visualizing simulations. [AppImage](https://docs.qgroundcontrol.com/master/en/getting_started/download_and_install.html) installation is recommended for Ubuntu and [Flatpak](https://flathub.org/apps/org.mavlink.qgroundcontrol) for Fedora.

## Running PX4 Autopilot in Gazebo Classic Simulator

	docker run -it --net=host -v ~/src/PX4-Autopilot:/src/PX4-Autopilot/:rw --name=sim px4io/px4-dev-simulation-focal:2023-06-26 bash
	cd src/
	git clone https://github.com/PX4/PX4-Autopilot.git
	cd PX4-Autopilot/
	HEADLESS=1 make px4_sitl gazebo-classic_standard_vtol
