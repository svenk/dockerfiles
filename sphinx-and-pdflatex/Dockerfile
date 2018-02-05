# Minimal Ubuntu 16.04 in a Docker image (http://phusion.github.io/)
FROM phusion/baseimage:0.9.22

MAINTAINER SvenK <https://github.com/svenk/dockerfiles>

RUN apt-get update \
 && apt-get install -y \
      wget \
      wput \
      curl \
      git \
      subversion \
      graphviz \
      make \
      python \
      python-pip \
      texlive-full \
      latexmk \
 && pip install sphinx \
  # Removing documentation packages *after* installing them is kind of hacky,
  # but it only adds some overhead while building the image.
 && apt-get --purge remove -y .\*-doc$ \ 
  # Remove more unnecessary stuff
 && apt-get clean -y \
 && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
