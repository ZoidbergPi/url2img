FROM ubuntu:eoan

# Set environment variables
ENV DEBIAN_FRONTEND noninteractive
RUN  sed -i s@/archive.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list

RUN  apt-get clean
# Install dependencies
RUN apt-get update -q && apt-get install -y xz-utils fontconfig ca-certificates

# add url2img binary
WORKDIR /
#ADD https://github.com/gen2brain/url2img/releases/download/1.3/url2img-1.3.tar.xz /

COPY url2img-1.3.tar.xz /
RUN tar xf /url2img-1.3.tar.xz

# add Fonts
RUN apt-get install -y language-pack-zh-hans
RUN apt-get install -y fonts-droid-fallback ttf-wqy-zenhei ttf-wqy-microhei fonts-arphic-ukai fonts-arphic-uming

# add entrypoint
ADD docker-entrypoint.sh /
RUN chmod +x /docker-entrypoint.sh

# start daemon
CMD ["/docker-entrypoint.sh"]
