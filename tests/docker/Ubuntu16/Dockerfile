FROM ubuntu:16.04

# Pre-install packages to speed IM contextualization
RUN apt-get update && \
    apt-get install -y \
            openssh-server \
            sshpass \
	    python \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN mkdir /var/run/sshd

RUN echo 'root:docker' | chpasswd

RUN sed -ri 's/^PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config

RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config

EXPOSE 22

CMD    /usr/sbin/sshd -D
