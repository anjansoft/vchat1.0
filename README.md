 
## Installation
 
```bash
$ cd server
$ npm install
```

* Copy `config.example.js` as `config.js` and customize it for your scenario:

```bash
$ cp config.example.js config.js
```

**NOTE:** To be perfectly clear, "customize it for your scenario" is not something "optional". If you don't set proper values in `config.js` the application **won't work**.

* Set up the mediasoup-demo browser app:

```bash
$ cd app
$ npm install
```


## Run it locally

* Run the Node.js server application in a terminal:

```bash
$ cd server
$ npm start
```

* In a different terminal build and run the browser application:

```bash
$ cd app
$ npm start
```

* Enjoy.


## Deploy it in a server

* Globally install `gulp-cli` NPM module (may need `sudo`):

```bash
$ npm install -g gulp-cli
```

* Build the production ready browser application:

```bash
$ cd app
$ gulp dist
```

* Upload the entire `server` folder to your server and make your web server (Apache, Nginx, etc) expose the `server/public` folder.

* Edit your `server/config.js` with appropriate settings (listening IP/port, logging options, **valid** TLS certificate, etc).

* Within your server, run the Node.js application by setting the `DEBUG` environment variable according to your needs ([more info](https://mediasoup.org/documentation/v3/mediasoup/debugging/)):

```bash
$ DEBUG="*mediasoup* *ERROR* *WARN*" node server.js
```
* If you wish to run it as daemon/service you can use [pm2](https://www.npmjs.com/package/pm2) process manager. Or you can dockerize it among other options.

* The Node.js application exposes an interactive terminal. When running as daemon (in background) the host administrator can connect to it by entering into the `server` folder and running:

```bash
$ npm run connect
```

## Run mediasoup server with Docker

* Required environment variables: [server/DOCKER.md](server/DOCKER.md).
* Build the Docker image: [server/docker/build.sh](server/docker/build.sh).
* Run the Docker image: [server/docker/run.sh](server/docker/run.sh).

```
$ cd server
$ docker/build.sh
$ MEDIASOUP_ANNOUNCED_IP=192.168.1.34 ./docker/run.sh
``` 
## License

MIT
