FROM ubuntu:14.04
MAINTAINER "Brant Faircloth" <brant _at_ faircloth-lab _dot_ org>
ENV container docker

# update yum
RUN dpkg --add-architecture i386
RUN apt-get update
RUN apt-get install -y libc6:i386 libncurses5:i386 libstdc++6:i386 zlib1g:i386

# install wget
RUN apt-get install -y wget tar bzip2

# add generic user
RUN useradd -ms /bin/zsh generic

# switch to generic user
USER generic
ENV HOME /home/generic
WORKDIR /home/generic/

# get wQMC and install
RUN mkdir -p $HOME/bin/wqmc
RUN cd $HOME/bin/wqmc && wget --no-check-certificate https://s3.faircloth-lab.org.s3.amazonaws.com/packages/wQMC.tar.gz
RUN cd $HOME/bin/wqmc && tar -xzvf wQMC.tar.gz
RUN ln -s $HOME/bin/wqmc/max-cut-tree $HOME/bin/max-cut-tree
RUN chmod 0755 $HOME/bin/wqmc/max-cut-tree
ENV PATH="$HOME/bin:$PATH"
