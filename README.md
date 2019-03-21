# My Mopidy Setup

This is the Docker image that I'm currently using to run [Mopidy](https://www.mopidy.com/) on a Raspberry Pi.

It probably won't be exactly the setup you want, but feel free to create a fork for your own setup.

Build:

```shell
docker build -t andrewcodes/mopidy .
docker build -t andrewcodes/mopidy -f Dockerfile.pi .
```

Run:

```shell
docker run -it --rm --device /dev/snd --name mopidy -p 6600:6600 -p 6680:6680 andrewcodes/mopidy
```

Run in background:

```shell
docker run -d --restart=unless-stopped --device /dev/snd --name mopidy -p 6600:6600 -p 6680:6680 andrewcodes/mopidy
```

View logs:

```shell
docker logs mopidy
```

Execute any Mopidy command:

```shell
docker exec mopidy mopidy <cmd>
docker exec mopidy mopidy config
docker exec mopidy mopidy deps
```
