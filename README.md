# Homelab

# Instructions
## Tailscale
Currently tailscale does not allow users to set api keys with no expiry. To avoid having keys expire I install tailscale on the OS and set the key to not expire. However I've kept the compose entry for documentation purposes.

## Graylog
Running mongo db on raspberry pi requires a manual download of the image. Follow the instructions [here](https://github.com/themattman/mongodb-raspberrypi-docker) to get the image which is used in the compose file

`cd mongo_image`

`wget https://github.com/themattman/mongodb-raspberrypi-docker/releases/download/r7.0.8-mongodb-raspberrypi-docker-unofficial/mongodb.ce.pi4.r7.0.8-mongodb-raspberrypi-docker-unofficial.tar.gz`

`docker load --input mongodb.ce.pi4.r7.0.8-mongodb-raspberrypi-docker-unofficial.tar.gz`

Graylog requires a few environment variables. I prefer not to have .env files in github repos to prevent the chances of leaking secrets. So, instead I supply the required variables with an environment file outside the repo. However, this requires the environment variables that reference local .env files to be commented out since the `env_file:` directive does not substitute in envs like local .env files do.
