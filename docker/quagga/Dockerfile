FROM andreymgn/base

RUN apt update
RUN apt upgrade -y

RUN wget https://snapshot.debian.org/archive/debian/20060317T000000Z/pool/main/libc/libcap/libcap1_1.10-14_amd64.deb && \
    wget https://snapshot.debian.org/archive/debian/20080709T000000Z/pool/main/q/quagga/quagga_0.99.10-1_amd64.deb


RUN DEBIAN_FRONTEND=noninteractive apt install -y \
	cron \
	logrotate

RUN DEBIAN_FRONTEND=noninteractive apt install -y \
    ./libcap1_1.10-14_amd64.deb \
    ./quagga_0.99.10-1_amd64.deb

RUN apt-mark hold quagga

RUN rm quagga_0.99.10-1_amd64.deb && rm libcap1_1.10-14_amd64.deb 

RUN apt clean

RUN chmod -R 777 /var/log/quagga
RUN ln /etc/init.d/quagga /etc/init.d/zebra
RUN ln -s /etc/quagga /etc/zebra

COPY zebra.conf /etc/quagga/zebra.conf
RUN chown quagga:quagga /etc/quagga/zebra.conf
RUN chmod 640 /etc/quagga/zebra.conf
