# Run Upwork Team App in a container
#
# docker run -it \
#       --cpuset-cpus 0 \ # control the cpu
#       --memory 512mb \ # max memory it can use
#       -u $(id -u) \ # current user id
#       -v /tmp/.X11-unix:/tmp/.X11-unix \ # mount the X11 socket
#       -e DISPLAY \
#       -v $HOME/.Upwork:/.Upwork \
#       --device /dev/snd \ # so we have sound
#       -v /dev/shm:/dev/shm \
#       --name upwork \
#       pshevtsov/upwork

FROM debian:jessie

MAINTAINER Petr Shevtsov <petr.shevtsov@gmail.com>

ENV VERSION v4_1_351_0_a7qf2qa9wn508n52

ADD http://updates.team.odesk.com/binaries/${VERSION}/upwork_amd64.deb /src/upwork_amd64.deb

RUN apt-get update && apt-get install -y \
    gconf-service \
    gksu \
    libasound2 \
    libatk1.0-0 \
    libcairo2 \
    libcups2 \
    libdbus-1-3 \
    libexpat1 \
    libfontconfig1 \
    libfreetype6 \
    libgconf-2-4 \
    libgtkglext1 \
    libnspr4 \
    libnss3 \
    libpango1.0-0 \
    libxss1 \
    libxtst6 \
    --no-install-recommends \
    && dpkg -i /src/upwork_amd64.deb \
    && rm -rf /var/lib/apt/lists/* \
    && rm -rf /src/*.deb

ENTRYPOINT ["upwork"]
