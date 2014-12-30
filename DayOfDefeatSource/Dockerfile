# Left4Dead2 Server repo
#
# VERSION 0.1

FROM debian:wheezy
MAINTAINER Dh0mp5eur

RUN apt-get update
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get -y install openssh-server supervisor gdb mailutils postfix lib32gcc1 expect wget vim htop

ENV USERNAME dodsserver
RUN adduser --disabled-password --gecos "" $USERNAME
ENV HOME /home/$USERNAME

ADD ./dodsserver /home/$USERNAME/
ADD ./cfg /home/$USERNAME/
RUN chmod +x /home/$USERNAME/$USERNAME
RUN chown -R $USERNAME:$USERNAME /home/$USERNAME/*

USER $USERNAME
WORKDIR /home/$USERNAME
RUN ./dodsserver auto-install

COPY supervisord.conf /etc/supervisor/con.d/supervisord.conf

EXPOSE 22 27015
CMD ["/usr/bin/supervisord"]
