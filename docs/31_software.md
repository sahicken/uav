# Software Team

In this section we begin to cover Intermediate topics of importance for Software Team members. All software team members and team leaders should be aware of what is documented here.

## Python 3

Python 3 will likely be used throughout our project. Check out the [official docs](https://docs.python.org/3/).

## QGroundControl (QGC) Mission Planner

QGroundControl or simply QGC is a frontend for mission planning and partially visualizing simulations. [AppImage](https://docs.qgroundcontrol.com/master/en/getting_started/download_and_install.html) installation is recommended for Ubuntu and [Flatpak](https://flathub.org/apps/org.mavlink.qgroundcontrol) for Fedora.

## Running PX4 Autopilot in Gazebo Classic Simulator

	docker run -it --net=host -v ~/src/PX4-Autopilot:/src/PX4-Autopilot/:rw --name=sim px4io/px4-dev-simulation-focal:2023-06-26 bash
	cd src/
	git clone https://github.com/PX4/PX4-Autopilot.git
	cd PX4-Autopilot/
	HEADLESS=1 make px4_sitl gazebo-classic_standard_vtol

## A Little More about Docker

Only the first command in the above codeblock is outside the container. Leave the container by running `exit`. Note that `docker run` creates a new container. To execute an existing container use `docker exec`. Also, stopped containers require running `docker start`. Combining these on Fedora (skip first command for Ubuntu/Debian) a workflow might look something more like this.

	sudo systemctl start docker
	docker start sim
	docker exec -it sim bash
	cd src/PX4-Autopilot/
	HEADLESS=1 make px4_sitl gazebo-classic_standard_vtol
	exit
	