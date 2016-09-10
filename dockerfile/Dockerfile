FROM centos
MAINTAINER Zhifeng Zhang "zzrotation@163.com"

RUN yum update

RUN yum install -y openssh-server sudo net-tools
RUN sed -i 's/UsePAM yes/UsePAM no/g' /etc/ssh/sshd_config

RUN useradd nbi
RUN echo "nbi:nbi1234" | chpasswd
RUN echo "nbi	ALL=(ALL)	ALL" >> /etc/sudoers

RUN echo "root:shroot" | chpasswd

RUN ssh-keygen -t dsa -f /etc/ssh/ssh_host_dsa_key
RUN ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key

RUN mkdir /var/run/sshd
EXPOSE 22


CMD ["/usr/sbin/sshd", "-D"]
