FROM andreymgn/base

COPY zebra.conf /etc/quagga/zebra.conf

RUN apt update && \
    apt upgrade -y && \
    wget https://snapshot.debian.org/archive/debian/20060317T000000Z/pool/main/libc/libcap/libcap1_1.10-14_amd64.deb && \
    wget https://snapshot.debian.org/archive/debian/20080709T000000Z/pool/main/q/quagga/quagga_0.99.10-1_amd64.deb && \
    DEBIAN_FRONTEND=noninteractive apt install -y \
        cron \
        logrotate \
        ./libcap1_1.10-14_amd64.deb \
        ./quagga_0.99.10-1_amd64.deb && \
    apt-mark hold quagga && \
    rm quagga_0.99.10-1_amd64.deb && \
    rm libcap1_1.10-14_amd64.deb && \
    apt clean && \
    chmod -R 777 /var/log/quagga && \
    ln /etc/init.d/quagga /etc/init.d/zebra && \
    ln -s /etc/quagga /etc/zebra && \
    chown quagga:quagga /etc/quagga/zebra.conf && \
    chmod 640 /etc/quagga/zebra.conf
