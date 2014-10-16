# boot2docker-powify

[Boot2docker] :heart: [Pow]

## What

`boot2docker-powify` sets up domain `foo-bar.dev` for a [Docker] container named `foo_bar`.

And `boot2docker-depowify` does the opposite.

## How

### To set up

```
$ docker ps
CONTAINER ID        IMAGE                     COMMAND               CREATED             STATUS              PORTS                    NAMES
e4e983e368f5        dockerfile/ghost:latest   "bash /ghost-start"   3 hours ago         Up 3 hours          0.0.0.0:2368->2368/tcp   loving_galileo

$ boot2docker-powify
Created /Users/uasi/Library/Application Support/Pow/Hosts/loving-galileo
Started forwarding port 2368
======> http://loving-galileo.dev is live

$ curl -s http://loving-galileo.dev | grep "<title>"
    <title>Ghost</title>
```

### To tear down

```
$ boot2docker-depowify
Removed /Users/uasi/Library/Application Support/Pow/Hosts/loving-galileo
Killed ssh with pid 16719
Stopped forwarding port 2368
======> http://loving-galileo.dev has gone

$ curl -s http://loving-galileo.dev | grep "<title>"
  <title>Application not found</title>
```

### To specify containers

```
$ boot2docker-powify         # powify all containers
$ boot2docker-powify foo bar # powify only foo and bar
```

## Who

[@uasi](https://twitter.com/uasi) (<uasi@uasi.jp>)

[Docker]: https://www.docker.com
[Boot2docker]: http://boot2docker.io
[Pow]: http://pow.cx
