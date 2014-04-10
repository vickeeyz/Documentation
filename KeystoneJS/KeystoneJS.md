# KeystoneJS

Before you begin, make sure you have [Node.js] (http://nodejs.org/download/) and MongoDB installed.

* Get Node.js source code for compilation from here: http://nodejs.org/download/

or 

* follow below step for quick setup of latest version.

### Node.js Installation Ubuntu

```
apt-get install python-software-properties
```

```
apt-add-repository ppa:chris-lea/node.js
```

```
apt-get update
```

```
node.js install
```

```
apt-get install nodejs
```

> Check node.js version

```
node -v
```

> Outputs

```
v0.10.20
```

```
npm install
```

> Above command should install npm.

> Check npm version

```
npm -v
```

> Outputs

```
1.4.3
```

> If for some reason, if you see npm is not installed, you may try running:

```
sudo apt-get install npm
```

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

> You can optionally ensure that MongoDB will start following a system reboot by issuing the following command:

```
sudo chkconfig mongod on
```

**Log File Path**: /var/log/mongo/mongod.log file.


### KeystoneJS Installation

* Install the generator

> You'll be using the KeystoneJS generator made with Yeoman. In your root directory run:

```
sudo npm install -g generator-keystone
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

> To connect to a server other than localhost, add a MONGO_URI setting to the .env file in your Keystone project directory:

```
MONGO_URI=mongodb://your-server/database-name
```