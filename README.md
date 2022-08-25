# Build project specific container

```{bash}
FROM joelgsponer/radian:4.1.3
# install released version
RUN sudo apt-get update -y
RUN sudo apt-get install -y python3
RUN sudo apt-get install -y python3-pip
RUN apt-get install fish -y
RUN pip3 install -U radian
RUN mkdir /renv/
RUN mkdir /renv/cache/
RUN RENV_PATHS_CACHE=/renv/cache/
WORKDIR /home/
CMD "radian"
```

# Build script

```{bash}
name=basename $PWD
docker build -t "joelgsponer/${name}" .
```
# Starting script

```{bash}
# the location of the renv cache on the host machine
RENV_PATHS_CACHE_HOST="/Users/${USER}/docker/renv"
# where the cache should be mounted in the container
RENV_PATHS_CACHE_CONTAINER="/renv/cache"
name=basename $PWD
# run the container with the host cache mounted in the container
docker run \
  -e "RENV_PATHS_CACHE=${RENV_PATHS_CACHE_CONTAINER}" \
  -v "${RENV_PATHS_CACHE_HOST}:${RENV_PATHS_CACHE_CONTAINER}" \
  -v "${PWD}:/home/" \
  -ti \
  --rm "joelgsponer/${name}" \
  radian
```
