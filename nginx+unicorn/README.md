# Unicorn proxy with Nginx

* clone and use the nginx.conf and sites-available conf from my repo

> Goto to nginx/sites-enabled directory and create a symlink to sites-available conf

```
cd /etc/nginx/sites-enabled
```

```
ln -s /etc/nginx/sites-available/appname appname
```

> Restart nignx

```
sudo service nginx restart
```

# For Unicorn configurations

> place the unicorn.rb in the app/config/

* create a unicorn directory in /etc

```
sudo mkdir /etc/unicorn 
```

> place the app.conf file in /etc/unicorn
> modify it as per your requirement

```
sudo nano /etc/unicorn/app.conf
```

> place the unicorn.sh script in /etc/init.d/
> save the script with name unicorn
> make the unicorn init script executable

```
chmod +x /etc/init.d/unicorn
```

```
update-rc.d unicorn defaults
```

Now start the unicorn service

```
sudo service unicorn restart
```
