FROM ubuntu:16.04

RUN apt-get update && apt-get install -y openssh-server
RUN mkdir /var/run/sshd

COPY ssh-pub-keys /tmp/ssh-pub-keys

RUN mkdir /root/.ssh
RUN cat /tmp/ssh-pub-keys/*.pub > /root/.ssh/authorized_keys


EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
