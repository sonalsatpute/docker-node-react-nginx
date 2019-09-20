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

___

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

hello-world url -> `http://localhost:3001/`

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

### Grab the IP address of docker-machine:

```shell script
$ docker-machine ip hello-world
```

### Then, build the images and run the container:

```shell script
$ docker build -t hello-world:dev .

$ docker run -v ${PWD}:/app -v /app/node_modules -p 3001:3000 --rm hello-world:dev
```

### Destroy the Machine: (hold this till end)

```shell script
$ eval $(docker-machine env -u)
$ docker-machine rm sample
```

## Live Enviroment Setup

### using docker file

```shell script
$ docker build -f Dockerfile-live -t hello-world:live .
$ docker run -it -p 80:80 --rm hello-world:live
```

### using docker compose

```shell script
$ docker-compose -f docker-compose-live.yml up -d --build
```