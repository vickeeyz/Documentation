# KeystoneJS

Before you begin, make sure you have [Node.js] (http://nodejs.org/download/) and MongoDB installed.

### MongoDB Installation Ubuntu

```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
```

```
echo 'deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen' | sudo tee /etc/apt/sources.list.d/mongodb.list
```

```
sudo apt-get update
```

```
sudo apt-get install mongodb-org
```

```
sudo service mongod start
```

```
sudo chkconfig mongod on
```

**Log File Path**: /var/log/mongo/mongod.log file.


### KeystoneJS Installation

* Install the generator

> You'll be using the KeystoneJS generator made with Yeoman. In your root directory run:

```
npm install -g generator-keystone
```

> Create a folder for your project

> Create your project wherever you want:

```
mkdir my-test-project
```

> Than make sure you're in your new project:

```
cd my-test-project
```

> Run the generator

```
yo keystone
```

> Run it in your command line like this:

```
node keystone
```

> Then open http://localhost:3000 to view it in your browser.