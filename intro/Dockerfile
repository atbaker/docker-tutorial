# Example dockerfile for a Two Scoops-style Django project
# https://github.com/atbaker/docker-tutorial | https://github.com/twoscoops/django-twoscoops-project

FROM ubuntu:precise

MAINTAINER Andrew T. Baker <andrew@andrewtorkbaker.com>

# Add the Django app to the container and install its requirements
ADD sd_sample_project /var/www/django
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y python-pip
RUN pip install virtualenv
RUN virtualenv /var/www/venv
RUN /var/www/venv/bin/pip install -r /var/www/django/requirements/production.txt

# Syncdb (a sqlite3 database for simplicity)
ENV PYTHONPATH $PYTHONPATH:/var/www/django/sd_sample_project
ENV DJANGO_SETTINGS_MODULE sd_sample_project.settings.production
ENV SECRET_KEY no-so-secret # Fix for your own site!
RUN /var/www/venv/bin/django-admin.py syncdb --migrate --noinput
RUN /var/www/venv/bin/django-admin.py collectstatic --noinput

# Create gunicorn log files
RUN mkdir /var/log/gunicorn
RUN touch /var/log/gunicorn/access.log
RUN touch /var/log/gunicorn/error.log

# Add project to PYTHONPATH
RUN echo PYTHONPATH=$PYTHONPATH:/var/www/django/sd_sample_project >> /root/.bashrc

# Clean up APT when done
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

EXPOSE 80

CMD /var/www/venv/bin/gunicorn sd_sample_project.wsgi:application --bind 0.0.0.0:80
