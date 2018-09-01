FROM centos:7.5.1804
RUN yum -y update && \
    yum reinstall -y glibc-common && \
    localedef -v -c -i ja_JP -f UTF-8 ja_JP.UTF-8; echo "";
ENV LANG=ja_JP.UTF-8
RUN yum -y install gcc zlib-devel bzip2 bzip2-devel readline readline-devel sqlite sqlite-devel openssl openssl-devel git && \
    curl -L https://raw.githubusercontent.com/pyenv/pyenv-installer/master/bin/pyenv-installer | bash && \
ENV PATH="/root/.pyenv/bin:$PATH"
RUN eval "$(pyenv init -)" && \
    eval "$(pyenv virtualenv-init -)" && \
    pyenv install 3.6.6 && \
    pyenv global 3.6.6 && \
    pip install pipenv \

CMD ["pipenv", "--version"]
