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

Software
--------

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

Most Linux distros running a desktop environment should work, however
[Fedora](https://docs.fedoraproject.org/en-US/fedora/latest/getting-started/)
or [Ubuntu](https://ubuntu.com/tutorials/install-ubuntu-desktop) will be
assumed. On Windows installing virtualization software such as
[VMware](https://en.wikipedia.org/wiki/VMware_Workstation_Player) or
[Virtualbox](https://en.wikipedia.org/wiki/VirtualBox) is necessary.
**WSL2 does not yet work with these instructions!** 12GB RAM or more is
highly recommended for virtualization. To reduce RAM requirements
consider installing either Lubuntu or Xubuntu.

After installing a supported distro, install docker using [these
instructions for Fedora](https://docs.docker.com/engine/install/fedora/)
or [the Ubuntu instructions
here](https://docs.docker.com/engine/install/ubuntu/). On Fedora you
**must** run `sudo systemctl start docker` after every reboot or instead
just [configure docker to start upon
boot](https://docs.docker.com/engine/install/linux-postinstall/#configure-docker-to-start-on-boot-with-systemd).
This is unnecessary for Ubuntu.

### note about sections

All sections should be limited to their most simple components in the
getting started section

Design
------

No design section in getting started yet.

Electronics
-----------

No electronics section either.

Teams
=====

Software Team
-------------

Design Team
-----------

Change the name of the design team to eliminate confusion between it and
the design portition of the competition.

Electronics Team
----------------

Software
========

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

Design
======

Insert 3D CAD file link.

Electronics
===========

Components list here. \# Design (Competition) \# Simulation \# Flight
