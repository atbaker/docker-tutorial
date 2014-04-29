Introductory docker tutorial
============================

This tutorial will help you get started using `docker <https://www.docker.io/>`_. In this tutorial, you will:

- Start online with the official docker quickstart materials
- Install docker on your machine (or use `Vagrant <http://www.vagrantup.com/>`_ and `Ansible <http://www.ansible.com/>`_) to get a working docker daemon
- Complete a Dockerfile to build a docker image for a sample `Django <https://www.djangoproject.com/>`_ app
- Use `Fig <http://orchardup.github.io/fig/?>`_ to more easily manage a docker-based development environment

Exercise 0: Setting up your development environment
---------------------------------------------------

Installing docker is more complicated than installing your average application, but fortunately the documentation is great. You have a few options:

- If you are doing this tutorial in one of my classes, you may want to use one of the cloud servers I have already provided. Ask me for the connection details.
- If you have `Vagrant <http://www.vagrantup.com/>`_ and `VirtualBox <https://www.virtualbox.org/>`_ installed, you can use the Vagrantfile in this repo to quickly provision your server:

  - Install Ansible if you haven't already. You have a few options on this page - I find apt, yum, or ``pip`` to be easiest: http://docs.ansible.com/intro_installation.html#latest-releases-via-pip
  - ``cd`` to the base directory of this repo
  - ``vagrant up`` to start your VM. It will install Docker automatically.
    - If you have port forwarding issues, try closing Chrome and then ``vagrant up``-ing again.
  - Connect to the VM with ``vagrant ssh``. This repo will be mounted in the VM at ``/vagrant``

- If you're using a Mac, you may want to use Boot2Docker instead: http://docs.docker.io/installation/mac/
- If you want to work natively in Linux, follow the appropriate instructions for your OS: http://docs.docker.io/installation/#installation

**If you're waiting on downloading / provisioning, continue to the next section.** You won't actually need your local environment until exercise 2.

Exercise 1: Docker and dockerfile basics
----------------------------------------

The official docker.io tutorials are the best way to ease in to working with docker. They are concise and informative. You should skim through them now before proceeding to exercise 2:

- Interactive command line tutorial: https://www.docker.io/gettingstarted/
- Dockerfile tutorial: https://www.docker.io/learn/dockerfile (if you're running behind, you can skip level 02)

Exercise 2: Fire it up!
-----------------------

It's time to start your first Docker containers!

    I won't provide all the answers here. To complete this (and future) exercises, you will need to use the Docker docs (http://docs.docker.io/) and your intuition!

Pull down this docker image from the docker index: ``atbaker/sd-django``

Start a container from this image using the ``docker run`` command. Don't forget to pass the correct options to publish port 80 to your localhost. Confirm that your container is running with the ``docker ps`` command.

If your container started successfully, you should be able to access the Django app at an address like http://localhost:49178/

Now let's say we wanted to update the navbar header on the homepage to be "Sample docker site" instead of "sd_sample_project". We need to edit the file in the container at ``/var/www/django/sd_sample_project/templates/base.html``.

Start a container with the ``atbaker/sd-django`` image again, this time in an interactive shell. Use a text editor of your choice to update the navbar text. Then exit the shell session.

    You rarely need to use the full container/image ID value when issuing commands to the docker client. Usually the first few characters are sufficient.

That edit was just to a single container. If we want that edit to be included next time we start a new container from this image, we need to commit the change to a new image.

Commit your change to a new image (use ``atbaker/sd-django`` or your own namespace), then create a new container from that image and check it out in a browser to make sure it worked.

That's the basics of working with containers and images. Before we move on to the next exercise, it's a good idea to stop your running containers with the ``docker stop`` command since we don't need them anymore.

Exercise 3: Dockerizing a Django app
------------------------------------

In the previous exericse updating the navbar text in the Django app was a somewhat tedious process. Even if we were using `git <http://git-scm.com/>`_ to version control our Django source code, you would still need to create a new container with a shell, update it, and then commit your changes to an image before you could deploy those changes anywhere else.

That's where `Dockerfiles <http://docs.docker.io/reference/builder/>`_ come in. Dockerfiles and the ``docker build`` command programatically build your docker images. If you keep your Dockerfile with your source code, you can include the latest source every time you build your docker image (perhaps with a Continuous Integration service).

In the **intro** subdirectory, you will find the source code for the sample Django project and a partially completed Dockerfile. **Complete the Dockerfile and use** ``docker build`` **to create a new image for this Django app.** Then create a container from that image to test if it works.

    There are some hints in the Dockerfile comments, but you'll want to reference the Dockerfile documentation as well: http://docs.docker.io/reference/builder/

Exercise 4: Using Fig to manage your development environment
------------------------------------------------------------

In exercise 3 you created a Dockerfile to help you build new docker images when you updated your source code. In this exercise you will learn how to use `Fig <http://orchardup.github.io/fig/index.html>`_ to make things even easier.

Fig is an open source Docker project that makes it easier to manage docker containers in your development environment. It was created by the people behind `Orchard <https://www.orchardup.com/>`_, a Docker hosting service.

Fig is written in Python and has a great tutorial for using Fig to manage a Django app and a PostgreSQL database. You should go through that tutorial: http://orchardup.github.io/fig/django.html

    If you aren't using one of my cloud servers or the Vagrant Box in this repo, then you will need to install Fig yourself. Instructions are here: http://orchardup.github.io/fig/install.html

What's next?
------------

Congratulations, you're now a budding dockeristo/a! If there is any swag left at the front of the class, you should grab some.

If you want to keep working with docker, check out the advanced tutorial in this repo for other cool projects to check out.
