Introduction
============

This is the official repository for Fullerton College's Applied
Engineering Club (AEC) UAV Project (2024). Welcome applied engineers!

What's the UAV Project?
-----------------------

The UAV Project is Fullerton College's entry into a design, simulation,
and flight competition with other schools. AEC members have decided to
submit a VTOL (vertical take off landing) Unmanned Aircraft Vehicle
(UAV).

Why should I Participate?
-------------------------

Participating in clubs gives students the experience needed to build
resumes and stand out from the competition when applying for
universities or jobs. Additionally it builds lifelong skills and friends
that are intrinsically valuable.

How do I Get More Involved?
---------------------------

Due to the public nature of the internet, this information is limited to
Fullerton College students only. Team Leaders for the UAV Project should
be contacted for details.

Where Can I Learn More?
-----------------------

The club discord and in person primarily. See answer above.

Getting Started
===============

This section is designed to simplify onboarding. Please be aware of the
structure of Project "Teams" as well, covered shortly.

Software
--------

Working on the Software Team effectively requires extensive knowledge of
multiple software stacks that have not entirley been listed, let alone
documented. I will continue to update this documenation. Please refer to
Discord for more up-to-date info.

### Project Docs

[Markdown](https://www.markdownguide.org/basic-syntax/) is the file
format of choice for UAV Project Docs because it's easy-to-learn and
well-supported on Github. Please use `pandoc docs/*.md -o README.md`
before submitting a pull request if it modifies any files in `docs/`.
Links to high-quality resources are located throughout this document,
including begineer resources such as [the Github
basics](https://docs.github.com/en/get-started). **Please use the
links!**

### Dependencies

Most Linux distros running a desktop environment should work for
beginning the UAV Project, however
[Fedora](https://docs.fedoraproject.org/en-US/fedora/latest/getting-started/)
or [Ubuntu](https://ubuntu.com/tutorials/install-ubuntu-desktop) will be
assumed. On Windows installing virtualization software such as
[VMware](https://en.wikipedia.org/wiki/VMware_Workstation_Player) or
[Virtualbox](https://en.wikipedia.org/wiki/VirtualBox) is necessary.
**WSL2 does not yet work with these instructions!** 12GB RAM or more is
highly recommended for virtualization. To reduce RAM requirements
consider installing either Lubuntu or Xubuntu.

After installing a supported distro, you can install docker using [these
instructions for Fedora](https://docs.docker.com/engine/install/fedora/)
or [the Ubuntu instructions
here](https://docs.docker.com/engine/install/ubuntu/). On Fedora you
**must** run `sudo systemctl start docker` after every reboot or instead
just [configure docker to start upon
boot](https://docs.docker.com/engine/install/linux-postinstall/#configure-docker-to-start-on-boot-with-systemd).
This is unnecessary for Ubuntu.

3D acceleration is unsupported on Docker for the UAV Project. You will
need to setup PX4 Autopilot to run Gazebo (Classic) under OpenGL by
running Ubuntu 20.04 or higher natively. This is especially important
for simulating Target Detection and Package Dropoff (Challenge).
Documentation has not been created at this time.

3D CAD
------

No 3D CAD Team section yet.

Electronics
-----------

No Electronics Team section either.

Teams
=====

This section more clearly defines the UAV Project teams and overall
internal structure of the UAV Project. We have been divided into 3 teams
by the Club President. Be mindful of the Project organization and goals
at all times. In order to effectively manage this project we need to be
in sync and informed properly. Know who to talk to about what and when
to not overload any AEC member. We all have to manage our school and
even work duties. Please stay in touch with your team leader regularly
and only go to the Club President for this project if needed.

Software
--------

This Github is a great place to be involved on the Software Team. Please
come to meeting and check our AEC Discord regularly! Welcome team!

3D CAD
------

Electronics
-----------

Software
========

In this section we begin to cover Intermediate topics of importance for
Software Team members. All software team members and team leaders should
be aware of what is documented here.

Python 3
--------

Python 3 will likely be used throughout our project. Check out the
[official docs](https://docs.python.org/3/).

QGroundControl (QGC) Mission Planner
------------------------------------

QGroundControl or simply QGC is a frontend for mission planning and
partially visualizing simulations.
[AppImage](https://docs.qgroundcontrol.com/master/en/getting_started/download_and_install.html)
installation is recommended for Ubuntu and
[Flatpak](https://flathub.org/apps/org.mavlink.qgroundcontrol) for
Fedora.

Running PX4 Autopilot in Gazebo Classic Simulator
-------------------------------------------------

    docker run -it --net=host -v ~/src/PX4-Autopilot:/src/PX4-Autopilot/:rw --name=sim px4io/px4-dev-simulation-focal:2023-06-26 bash
    cd src/
    git clone https://github.com/PX4/PX4-Autopilot.git
    cd PX4-Autopilot/
    HEADLESS=1 make px4_sitl gazebo-classic_standard_vtol

A Little More about Docker
--------------------------

Only the first command in the above codeblock is outside the container.
Leave the container by running `exit`. Note that `docker run` creates a
new container. To execute an existing container use `docker exec`. Also,
stopped containers require running `docker start`. Combining these on
Fedora (skip first command for Ubuntu/Debian) a workflow might look
something more like this.

    sudo systemctl start docker
    docker start sim
    docker exec -it sim bash
    cd src/PX4-Autopilot/
    HEADLESS=1 make px4_sitl gazebo-classic_standard_vtol
    exit

3D CAD Team
===========

Here's our current [model](https://a360.co/3ufcpI2)

We may or may not be covering mission planning on this team.

Electronics Team
================

This is our
[components](https://docs.google.com/spreadsheets/d/1Tah2RrGbtXM58vIQXKMKE_LqVQVQTJHqW0JtdlxkLvY/edit?usp=sharing)
list.

We will be running PX4 Autopilot on the Pixhawk (with missions uploaded
at the least).

It will be connected to a Raspberry Pi running ROS (with ROS nodes for
Obstacle Avoidance and Target Detection using
[OpenCV)](https://pypi.org/project/opencv-python/) as a companion
computer.

Competition
===========

The UAV competition is due in 3 pieces

Design
------

May 2024

Simulation
----------

May 2024

Flight
------

June 2024, both manned and unmanned (3 challenges).

Design
======

Simulation
==========

Gazebo and Gazebo Classic are the 2 main simulators under consideration.
Gazebo Classic runs on older Ubuntu (such as 20.04) and Gazebo on newer
(22.04).

Flight
======

Challenges
==========

The UAV Competion has 3 challenges (1 - easiest to 3 - hardest)

1.  Waypoint Navigation
2.  Obstacle Avoidance
3.  Target Detection and Package Dropoff

We will need to complete these Unmanned and Manned.

Waypoint Navigation
===================

This is relatively straightforward. Check out QGS.

Obstacle Avoidance
==================

[check out its github](https://github.com/PX4/PX4-Avoidance/tree/master)

We will need to figure out a way to commuicate a 3D Point Cloud
(i.e. [sensor\_msgs::PointCloud2](https://docs.ros.org/en/melodic/api/sensor_msgs/html/msg/PointCloud2.html))
with our sensors (Camera and perhaps an ultrasonic sensor) and ROS
nodes. One idea is [Rviz](http://wiki.ros.org/rviz/DisplayTypes/Camera).
[Research nodes please!](https://index.ros.org/)

Target Detection and Package Dropoff
====================================

This will require OpenCV from the rpi camera module (wide angle plus
lens).

[Offboard mode](https://docs.px4.io/main/en/flight_modes/offboard.html)
is under consideration.

[This is a starting
point](https://circuitcellar.com/research-design-hub/write-an-object-tracking-drone-application/)
