# Unicorn proxy with Nginx

* Download the nginx.conf and sites-available conf from my repo

```
cd /etc/nginx/
```

```
wget https://raw.github.com/vickeeyz/scripts/master/nginx+unicorn/nginx/nginx.conf
```

```
cd /etc/nginx/sites-available/
```

```
wget https://raw.github.com/vickeeyz/scripts/master/nginx+unicorn/nginx/sites-available/appname
```

**NOTE:** Make sure to open and edit the conf to replace appname with your appname

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

```
cd /home/user/sites/appname/config/
```

```
wget https://raw.github.com/vickeeyz/scripts/master/nginx+unicorn/unicorn/unicorn.rb
```

* create a unicorn directory in /etc

```
sudo mkdir /etc/unicorn 
```

> download the app.conf file in /etc/unicorn

```
cd /etc/unicorn/
```

```
wget https://raw.github.com/vickeeyz/scripts/master/nginx+unicorn/unicorn/appname.conf
```

> modify it as per your requirement

```
sudo nano /etc/unicorn/app.conf
```

> download the unicorn.sh script in /etc/init.d/

```
cd /etc/init.d/
```

```
wget https://raw.github.com/vickeeyz/scripts/master/nginx+unicorn/unicorn/unicorn.sh
```

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
