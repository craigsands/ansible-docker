FROM centos:centos7

RUN yum -y update; yum clean all
RUN yum -y install openssh-server passwd; yum clean all

# Add public key to authorized_keys
ADD ./ssh_host_rsa_key.pub /home/user/.ssh/authorized_keys

ADD ./start.sh /start.sh
RUN mkdir /var/run/sshd

RUN ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key -N '' 

RUN chmod 755 /start.sh
# EXPOSE 22
RUN ./start.sh
ENTRYPOINT ["/usr/sbin/sshd", "-D"]