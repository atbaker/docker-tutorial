Advanced docker tutorial
========================

This tutorials is for people who already understand the basics of using docker. 

It's not really a lesson with exercises - it's more a survey of different projects and services that are using docker to do something new. My goal with this tutorial is to provide jumping off points so you can learn more about what interests you the most.

You can also use this opportunity to talk with the other people here who are already using docker. With new tech like docker evolving so quickly, we all have something to teach each other.

Drone
-----

`Drone <https://drone.io/>`_ is a new open source docker based Continuous Integration service built with Go. It's under very active development and has a pretty substantial feature set for being a young project.

- GitHub: https://github.com/drone/drone
- Installation: http://drone.readthedocs.org/en/latest/setup.html

Go ahead and check out Drone. You can try to install it yourself if you follow the documentation on ReadtheDocs. If you need a sample Django project, you can use the ``sd_sample_project`` in this directory.

Deis
----

When docker was first released its most obvious application was powering Platform-as-a-Service (PaaS) tools. `Dokku <https://github.com/progrium/dokku>`_ was one of the first to hit it big, but now all eyes are on `Flynn <https://flynn.io/>`_ and `Deis <http://deis.io/>`_.

Both projects are still under active development, but the impression I get is that Deis is aiming for a "batteries included" approach, whereas Flynn will be more modular and customizable.

Because Deis is a little easier to set up, I recommend experimenting with it today.

- Github: https://github.com/deis/deis
- Installation: http://deis.io/get-deis/

Tutum
-----

Docker's killer feature is that it makes your apps perfectly portable. So it makes sense that docker's popularity would spawn a market for docker container hosting services. `Tutum <http://www.tutum.co/>`_ and `Orchard <https://www.orchardup.com/>`_ are some of the first to gain prominence.

Both are aiming for an underserved portion of the hosting market: People who don't want to manage the OS-level hassles of EC2 or DigitalOcean droplets, but want more control over how their app is run than they have with Heroku. With docker, developers can package up their apps in docker images and then deploy them everywhere with confidence. 

I have experimented with Tutum and found them easy to use. Like Orchard, they offer some stock docker images to help you get started.

http://www.tutum.co/

    **DISCLAIMER:** Tutum is providing an additional $15 worth of hosting credit to people who attend this tutorial. They also give me a little extra credit for reviewing their service. Free credit aside, however, I would still recommend trying it.

Docker API
----------

Docker's API is easy to work with and the `docker-py <https://github.com/dotcloud/docker-py>`_ wrapper is also very good. If you want to get your hands dirty working with the docker API, you can try building your own micro Platform-as-a-Service (PaaS). Here's a sample problem:

    Your company is having problems with demo servers. Your developers often need to spin up full EC2 instances to showcase new features to other parts of the company. You want to build a small app that could spin up demo servers for any given feature branch in your GitHub repo. You're going to use Docker to do it.

If you want to see a simple example of what a Flask and Docker-powered PaaS looks like, check out my side project, spin-docker: https://github.com/atbaker/spin-docker
