# My Mopidy Setup

This is the Docker image that I'm currently using to run [Mopidy](https://www.mopidy.com/) on a Raspberry Pi.

It probably won't be exactly the setup you want, but feel free to create a fork for your own setup.

## Build Your Own

```shell
docker build -t yourUser/mopidy .
docker build -t yourUser/mopidy:pi -f pi.Dockerfile .
```

## Mopidy Config

Place `mopidy.conf` file in `./config`

## Run

```shell
docker run -it --rm --device /dev/snd --mount type=bind,src=`$(PWD)/config`,dst=/root/.config/mopidy --name mopidy -p 6600:6600 -p 6680:6680 andrewcodes/mopidy:pi
```

## Run in background

```shell
docker run -d --restart=unless-stopped --device /dev/snd --mount type=volume,src=`$(PWD)/config`,target=/root/.config/mopidy --name mopidy -p 6600:6600 -p 6680:6680 andrewcodes/mopidy:pi
```

## View logs

```shell
docker logs mopidy
```

## Execute any Mopidy command

```shell
docker exec mopidy mopidy <cmd>
docker exec mopidy mopidy config
docker exec mopidy mopidy deps
```
