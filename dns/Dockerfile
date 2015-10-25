FROM ubuntu:14.04
RUN apt-get update
RUN apt-get install -y samba
RUN apt-get clean
RUN useradd -m toru
RUN echo toru:toru | chpasswd
RUN printf 'toru\ntoru\n' | pdbedit -a toru -t
COPY smb.conf /etc/samba/smb.conf
CMD /usr/sbin/smbd -F
