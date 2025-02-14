FROM mcr.microsoft.com/vscode/devcontainers/base:ubuntu-22.04

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && \
    apt-get install -y autoconf autopoint binutils clang cmake gettext git gperf libc++-dev libc++abi-dev libtool make nasm pkg-config po4a

RUN mkdir /ImageMagick6
RUN chown vscode.vscode /ImageMagick6

USER vscode
RUN mkdir /ImageMagick6/dependencies 
WORKDIR /ImageMagick6/dependencies

RUN git clone --depth 1 https://gitlab.com/libtiff/libtiff
RUN git clone --depth 1 https://github.com/strukturag/libde265
RUN git clone --depth 1 https://github.com/strukturag/libheif
RUN git clone --depth 1 https://github.com/uclouvain/openjpeg
RUN git clone --depth 1 https://github.com/webmproject/libwebp
RUN git clone --depth 1 https://github.com/madler/zlib
RUN git clone --depth 1 https://github.com/libjpeg-turbo/libjpeg-turbo
RUN git clone --depth 1 https://github.com/xz-mirror/xz
RUN git clone --depth 1 https://github.com/libraw/libraw
RUN git clone --depth 1 https://github.com/pnggroup/libpng
RUN git clone --depth 1 https://github.com/mm2/Little-CMS
RUN git clone --depth 1 https://github.com/freetype/freetype
RUN git clone --depth 1 https://gitlab.com/federicomenaquintero/bzip2.git
RUN git -c http.sslVerify=false clone https://www.cl.cam.ac.uk/~mgk25/git/jbigkit

RUN curl https://raw.githubusercontent.com/ImageMagick/ImageMagick6/main/.devcontainer/build_dependencies.sh -o build_dependencies.sh && \
    chmod +x build_dependencies.sh

ENV SRC=/ImageMagick6/dependencies
ENV WORK=/ImageMagick6
ENV PATH=$PATH:/ImageMagick6/bin
ENV LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/ImageMagick6/lib
ENV CXX=clang++
ENV CC=clang
RUN ./build_dependencies.sh