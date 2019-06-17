FROM centos:7

MAINTAINER Sylvain Girod (sylvain.girod@ynov.com)
ENV container docker
RUN (cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == \
systemd-tmpfiles-setup.service ] || rm -f $i; done); \
rm -f /lib/systemd/system/multi-user.target.wants/*;\
rm -f /etc/systemd/system/*.wants/*;\
rm -f /lib/systemd/system/local-fs.target.wants/*; \
rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
rm -f /lib/systemd/system/basic.target.wants/*;\
rm -f /lib/systemd/system/anaconda.target.wants/*;

RUN yum -y install openssh-server
RUN yum -y install mysql
RUN yum -y install httpd php php-mysql php-gd openssl psmisc tar

VOLUME [ "/sys/fs/cgroup" ]

EXPOSE 22 80
#RUN cp /lib/systemd/system/sshd.service /etc/systemd/system/multi-user.target.wants/
RUN cp /lib/systemd/system/httpd.service /etc/systemd/system/multi-user.target.wants/
COPY passwd /etc
COPY shadow /etc	
RUN echo 'lead_developer' | passwd lead_developer --stdin
RUN ssh-keygen -f /etc/ssh/ssh_host_rsa_key -N '' -t rsa
RUN ssh-keygen -f /etc/ssh/ssh_host_ed25519_key -N '' -t ed25519
RUN ssh-keygen -f /etc/ssh/ssh_host_ecdsa_key -N '' -t ecdsa
RUN echo PermitRootLogin yes >> /etc/ssh/sshd_config
#CMD ["/usr/sbin/sshd","-D, "-d", "-d", "-d"]
#CMD ["/bin/bash"]
CMD ["/usr/sbin/init"]

