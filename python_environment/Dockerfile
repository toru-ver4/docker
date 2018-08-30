FROM centos:7.5.1804
RUN yum -y update && \
    yum reinstall -y glibc-common && \
    localedef -v -c -i ja_JP -f UTF-8 ja_JP.UTF-8; echo "";
ENV LANG=ja_JP.UTF-8
RUN yum install -y https://centos7.iuscommunity.org/ius-release.rpm && \
    yum install -y python36 && \
    yum install -y python36u-pip && \
    pip3.6 install pipenv
CMD ["pipenv", "--version"]
