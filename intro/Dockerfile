# Example dockerfile for a Two Scoops-style Django project
# https://github.com/atbaker/docker-tutorial | https://github.com/twoscoops/django-twoscoops-project

# All Dockerfiles start from a base image. In this case, Ubuntu 12.04 LTS
FROM ubuntu:precise

# Add yourself as maintainer
MAINTAINER 

# The ENV command applies environment variables to the rest of the build steps.
# Add these environment variables to the build:
#   PYTHONPATH=$PYTHONPATH:/var/www/django/sd_sample_project
#   DJANGO_SETTINGS_MODULE=sd_sample_project.settings.production
#   SECRET_KEY no-so-secret # Fix for your own site!

# Add a command to copy the sd_sample_project to the /var/www/django directory
# in the image
# (your command here)

# Install pip and requirements
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y python-pip
RUN pip install virtualenv
RUN virtualenv /var/www/venv
RUN /var/www/venv/bin/pip install -r /var/www/django/requirements/production.txt

# Syncdb (a sqlite3 database for simplicity)
RUN /var/www/venv/bin/django-admin.py syncdb --migrate --noinput
RUN /var/www/venv/bin/django-admin.py collectstatic --noinput

# Create gunicorn log files
RUN mkdir /var/log/gunicorn
RUN touch /var/log/gunicorn/access.log
RUN touch /var/log/gunicorn/error.log

# Clean up APT when done
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Add a command to expose port 80 to the host container
# (your command here)

# Add a CMD statement to start the gunicorn server. The basic command is:
# /var/www/venv/bin/gunicorn sd_sample_project.wsgi:application
# (your command here)

# HINT: You also need to use the --bind option to tell gunicorn to respond to
# requests from all hosts, since all incoming requests through docker will
# appear to be from another machine.
