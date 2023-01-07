# mecanisoft
ARG BUILD_FROM
FROM $BUILD_FROM

ENV LANG C.UTF-8
ENV RYGEL_CACHE_DIR=/root/.cache/rygel \
    RYGEL_VIDEOS_DIR=/videos \
    RYGEL_MUSIC_DIR=/music \
    RYGEL_PICTURES_DIR=/pictures


SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Copy data for add-on
COPY rootfs /

# Install snapcast
RUN sed -i -e 's/v[[:digit:]]\..*\//edge\//g' /etc/apk/repositories

RUN apk update
RUN apk upgrade
RUN apk add --no-cache pulseaudio
RUN apk add --no-cache htop
RUN apk add --no-cache python3
RUN apk add --no-cache python3-pip  
RUN apk add --no-cache rygel
RUN apk add --no-cache bash
RUN apk add --no-cache tumbler
RUN apk add --no-cache gstreamer1.0-plugins-base
RUN apk add --no-cache gstreamer1.0-plugins-good
RUN apk add --no-cache gstreamer1.0-plugins-bad
RUN apk add --no-cache gstreamer1.0-plugins-ugly
RUN apk add --no-cache gstreamer1.0-libav
RUN apk add --no-cache openrc
RUN apk add --no-cache snapcast snapcast-server snapcast-client
RUN apk add --no-cache librespot
RUN apk add --no-cache alsa-plugins-pulse

VOLUME ["${RYGEL_CACHE_DIR}", "${RYGEL_VIDEOS_DIR}", "${RYGEL_MUSIC_DIR}", "${RYGEL_PICTURES_DIR}"]
