## Development
1. Install [Vagrant](https://www.vagrantup.com/downloads.html)
2. Install [VirtualBox](https://www.virtualbox.org)
3. Clone this repository
4. `cp config/config_example.js config/config.js`
5. Open `config/config.js` and enter desired values
6. `vagrant up`

##### Run tests:
Simply run: `make vm:test`

This will SSH into the VM and run the mocha tests.

##### Start the server:

To run the server on your VM, you have to options. To run it and see all the logging statements on your screen, just type `make vm:server`.

To start the server in the "background" with [PM2](https://github.com/Unitech/pm2), just type: `make start`.

## Production
We're running Ubuntu 14.04LTS in production. The `provision.sh` script should install and setup everything you need to run the app, as long as you put the repository in `/var/www/kenthackenough`.

1. Clone this repository
1. `cp config/config_example.js config/config.js`
1. Open `config/config.js` and enter desired values
1. `./provision.sh`
1. `npm install`
1. `npm rebuild`
1. `make start`

## Make commands
There are several `make` commands available to make your life easier. Here they are:
```
make test    # Runs tests
make server  # Runs a debugging server
make start   # Starts the pm2 process
make stop    # Stops the pm2 process
```
These tests all act on your local machine. If you would like to run the same commands on the Vagrant VM without SSHing, just prepend `vm:` to the command, like this:
```
make vm:test   # SSHs into the VM, runs all the tests, and then closes the connection
make vm:start  # Starts the pm2 process on the VM
...
```