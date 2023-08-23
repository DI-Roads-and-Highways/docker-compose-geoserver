## Table of Contents
1. [Prerequisites](#1-prerequisites)
1. [How to Use](#2-how-to-use)
1. [GeoServer Versions](#3-geoserver-versions)

## 1. Prerequisites
You will need to ensure that the following has been installed on the machine where the docker container is to be hosted:
- git (to clone this repo)
- docker
- docker-compose

## 2. How to Use
Follow these steps to get the GeoServer docker container running with the help of this repository:
1. Clone this repository to the machine.
1. We usually start GeoServer with an existing data directory, instead of a blank one, to save time setting up the workspaces, styles, layers, etc. If you want to do this, ensure you have a copy of the data directory in the correct location (as indicated in the `docker-compose.yml` file, this location is `$HOME/geoserver_data`, but if it's in a different location you may also enter the correct path in the YML file instead).
1. From a terminal with the working directory set to the location of these files, run `docker-compose up -d`.
    - You can also run this from a nother working directory if you specify the path the the `docker-compose.yml` file, please refer to the docker-compose documentation for how to do this.
1. Once the server is up and running, you may confirm that you are able to connect, and then start using it.

If updates need to be made to the configuration in future, one should
1. Run `docker-compose down` (again in the appropriate working directory as mentioned above) to stop the container.
1. `git pull` the repo to update the configuration files.
    - If you edited the `docker-compose.yml` file, you will need to revert them (you could make a copy first to compare with in case you need to re-apply your changes for the `git pull` to work).
1. Check for changes and make updates to the files if needed (e.g. re-applying your changes the were reverted before the pull).
1. Run `docker-compose up -d` to start the container with the updated configuration.

## 3. GeoServer Versions
This repository is currently to be used to start up a GeoServer v2.17.1 container. For now, this is the only version supported.

In future, we plan to update the files in the main branch to use images that include newer GeoServer versions. With each version bump, the plan is to first make a branch with the files for the current version - e.g. when moving to GeoServer v2.19.x, we will first make a branch to keep the files for GeoServer v2.17.1, so they remain accessible.