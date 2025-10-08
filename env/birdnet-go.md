# A Simple Howto Setup Birdnet-Go
*This document shows you how to setup Birdnet-Go in Linux*


## Requirements
* Linux based OS: Ubuntu, CachyOS..etc.
* Installed utility: docker, docker-compose, git
* USB microphone


## Installation
1. Install based OS of your choice: Ubuntu, CachyOS..etc
2. Install these packages
  2.1 Docker
  2.2 [`docker-compose`][1]
  2.3 `git`

## Get birdnet-go and spin it up
```bash
# cd to your favorite place to check out a source code repo
cd ~/src
git clone https://github.com/tphakala/birdnet-go
cd birdnet-go

# cp the default docker-compose.yml
cp Docker/docker-compose.yml .

# get the nightly docker image
docker-compose pull
docker-compose up -d
```

`birdnet-go` is now serving on port `8080`. You can browse the Web UI via a web browser at http://localhost:8080

### Initial Setup
1. Once you are on the webpage, you can set up your microphone device by goto Settings -> Audio Capture -> Sound Card
Source. Select your USB microphone, or built-in one if you want to use the built-in one.

2. Restart your docker
```bash
docker-compose restart birdnet-go
```

Now your `birdnet-go` will listen to the sound from the selected microphone and ID the bird.


[1]: https://github.com/docker/compose/release
[2]: https://github.com/tphakala/birdnet-go
