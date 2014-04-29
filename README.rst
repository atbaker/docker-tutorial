Docker 101 Tutorials
====================

These tutorials accompany `a short presentation given at April's Django District <http://slides.com/atbaker/docker-101>`_.

This repo includes a `Vagrantfile <http://www.vagrantup.com/>`_ and `Ansible playbook <http://www.ansible.com/>`_ which provision a docker daemon on an Ubuntu 14.04 LTS server to minimize time students spend configuring their environments.

Introductory tutorial
---------------------

This tutorial is for people new to `docker <https://www.docker.io/>`_. It covers:

- Docker basics
- Dockerizing your own apps
- Managing your development environment with `Fig <http://orchardup.github.io/fig/?>`_

See the **intro** subdirectory to get started.

Advanced tutorial
-----------------

For people who have used docker before. It includes a survey of different docker projects, plus an exercise to get you working with the docker API. Students will:

- Learn how to use `Drone <https://drone.io/>`_, `Deis <http://deis.io/>`_, and `Tutum <http://www.tutum.co/>`_
- Use the docker API and git commit hooks to automatically run Selenium acceptance tests
- Discuss how you're using docker with other folks

See the **advanced** subdirectory to get started.
