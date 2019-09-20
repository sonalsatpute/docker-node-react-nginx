# docker-node-react-nginx

  yarn start
    Starts the development server.

  yarn build
    Bundles the app into static files for production.

  yarn test
    Starts the test runner.

  yarn eject
    Removes this tool and copies build dependencies, configuration files
    and scripts into the app directory. If you do this, you can’t go back!

## Docker

### Build and tag the Docker image:

```shell script
$ docker build -t hello-world:dev .
```

### List docker image

```shell script
$ docker images
``` 

### Spin up the container once the build is done:

```shell script
$ docker run -v ${PWD}:/app -v /app/node_modules -p 3001:3000 --rm hello-world:dev
```

hello-world url -> `http://localhost:3001/`

## Docker compose 

### Build the image and fire up the container:

```shell script
$ docker-compose up -d --build
```

### Bring down the container

```shell script
$ docker-compose stop
```

## Docker Machine

### Create a new Machine:
   
```shell script
$ docker-machine create -d virtualbox hello-world

$ docker-machine env hello-world

$ eval $(docker-machine env hello-world)
```


___