### Server Scripts

* AWS Cloudformation Templates:

> AutoScaling-MultipleZones-LoadBalanced.template

> AutoScaling-MultipleZones-LoadBalanced-Notifications.template

* Lamp-Stack

> lamp-stack-MultiZone.template

> lamp-stack-single-instance.template

> lamp-stack-single-instance-with-RDS.template

* RubyonRails

> Rails-Multi-AZ.template

> Rails-Single-Instance.template

> Rails-Single-Instance-With-RDS.template

* Redis Configuration:

> redis.conf

* Sidekiq init script:

> sidekiq.sh

* Nginx+Unicorn configurations

> nginx.conf

>> /etc/nginx/sites-available/app.conf

> /etc/init.d/unicorn.sh

> /etc/unicorn/app.conf(for multiple apps running on unicorn)

> sites/app/config/unicorn.rb

* Monit monitoring for following services :

> monitrc

> /etc/monit/conf.d/services.conf

>> nginx

>> unicorn

>> postgresql

>> mysql

>> memcached

>> php5-fpm

* Vagrant Setup Guide

> Setup Ubuntu 12.04 LTS server on Vagrant

