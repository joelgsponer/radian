# Example Usage
```{bash}
# the location of the renv cache on the host machine
RENV_PATHS_CACHE_HOST="/Users/${USER}/docker/renv"

# where the cache should be mounted in the container
RENV_PATHS_CACHE_CONTAINER="/renv/cache"
echo "${RENV_PATHS_CACHE_HOST}:${RENV_PATHS_CACHE_CONTAINER}"

# run the container with the host cache mounted in the container
docker run \
  -e "RENV_PATHS_CACHE=${RENV_PATHS_CACHE_CONTAINER}" \
  -v "${RENV_PATHS_CACHE_HOST}:${RENV_PATHS_CACHE_CONTAINER}" \
  -v "${PWD}:/home/" \
  -ti \
  --rm joelgsponer/radian4.3.1 \
  radian
```
