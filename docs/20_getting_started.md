# Getting Started

This section is designed to simplify onboarding. Please be aware of the structure of Project "Teams" as well, covered shortly.

## Software Team

Working on the Software Team effectively requires extensive knowledge of multiple software stacks that have not entirley been listed, let alone documented. I will continue to update this documenation. Please refer to Discord for more up-to-date info.

### Project Docs

[Markdown](https://www.markdownguide.org/basic-syntax/) is the file format of choice for UAV Project Docs because it's easy-to-learn and well-supported on Github. Please use `pandoc docs/*.md -o README.md` before submitting a pull request if it modifies any files in `docs/`. Links to high-quality resources are located throughout this document, including begineer resources such as [the Github basics](https://docs.github.com/en/get-started). **Please use the links!**

### Dependencies

[QGroundControl](http://qgroundcontrol.com/) is current mission planning software used by this project. Without hardware, you must use some kind of simulator. Additionally, even with working hardware, running a fully constructed drone during development runs the risk of damaging expensive equipment. I recommend running the simulator with HEADLESS=1 (no gui) preprended to whatever ```make``` build you choose unless serious visualization is necessary, particularly if running non-natively. The GUI version of the simulator requires significant graphical horsepower using OpenGL.

Most Linux distros running a desktop environment should work for beginning the UAV Project's PX4 simulation, however [Fedora](https://docs.fedoraproject.org/en-US/fedora/latest/getting-started/) or [Ubuntu](https://ubuntu.com/tutorials/install-ubuntu-desktop) will be assumed. On Windows installing virtualization software such as [VMware](https://en.wikipedia.org/wiki/VMware_Workstation_Player) or [Virtualbox](https://en.wikipedia.org/wiki/VirtualBox) is necessary. **WSL2 does not yet work with these instructions!** 12GB RAM or more is highly recommended for virtualization. To reduce RAM requirements consider installing either Lubuntu or Xubuntu.

After installing a supported distro, you can install docker using [these instructions for Fedora](https://docs.docker.com/engine/install/fedora/) or [the Ubuntu instructions here](https://docs.docker.com/engine/install/ubuntu/). On Fedora you **must** run `sudo systemctl start docker` after every reboot or instead just [configure docker to start upon boot](https://docs.docker.com/engine/install/linux-postinstall/#configure-docker-to-start-on-boot-with-systemd). This is unnecessary for Ubuntu.

3D acceleration is unsupported on Docker for the UAV Project. You will need to setup PX4 Autopilot to run Gazebo (Classic) under OpenGL by running Ubuntu 20.04 or higher **natively**. This is especially important for simulating Target Detection and Package Dropoff (Challenge). Minimal documentation has been created for many of the later challenges.

For a more accurate simulation, use a [Raspberry Pi with Ubuntu running ROS](https://wiki.ros.org/ROSberryPi) during the simulation. The likely goal here is to have camera input from [ROS 2 affect behavior on the PX4 Simulator](https://docs.px4.io/main/en/ros/ros2.html) over PX4's best supported [middleware](https://docs.px4.io/main/en/middleware/uxrce_dds.html). This is necessary to enable Obstacle Avoidance.

### Using GitHub

You should get more familiar with git. Atlassian has a solid [cheat sheet.](https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet).
