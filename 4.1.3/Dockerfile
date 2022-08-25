FROM rocker/tidyverse:4.1.3
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

