FROM ubuntu:bionic
RUN apt-get update && apt-get install -y curl qemu unzip
WORKDIR /home/ubuntu
RUN curl -LO https://github.com/dhruvvyas90/qemu-rpi-kernel/raw/master/versatile-pb.dtb
RUN curl -LO https://github.com/dhruvvyas90/qemu-rpi-kernel/raw/master/kernel-qemu-4.19.50-buster
RUN curl -LO http://ftp.jaist.ac.jp/pub/raspberrypi/raspbian_lite/images/raspbian_lite-2019-06-24/2019-06-20-raspbian-buster-lite.zip
RUN unzip 2019-06-20-raspbian-buster-lite.zip
EXPOSE 10022
ENTRYPOINT ["qemu-system-arm", "-cpu", "arm1176", "-m", "256", "-nographic", "-M", "versatilepb", "-dtb", "/home/ubuntu/versatile-pb.dtb", "-net", "nic", "-net", "user,hostfwd=tcp::10022-:22", "-kernel", "/home/ubuntu/kernel-qemu-4.19.50-buster", "-append", "root=/dev/sda2 panic=1 rootfstype=ext4 rw", "-hda", "/home/ubuntu/2019-06-20-raspbian-buster-lite.img"]
