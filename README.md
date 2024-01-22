# QEMURPI-3B
用QEMU模拟RPI3B，启动脚本MacOS版本
安装好QEMU
下载镜像后复制bcm2710-rpi-3-b.dtb重命名dtb.dtb,复制kernel8.img重命名kernel.img
弹出boot镜像，把镜像复制到同脚本目录，重命名disk.img
打开终端，cd 你的脚本和镜像目录，先运行./resize-8G 然后运行./start
# Windows
安装好QEMU
下载镜像后复制bcm2710-rpi-3-b.dtb重命名dtb.dtb,复制kernel8.img重命名kernel.img
弹出boot镜像，把镜像复制到同脚本目录，重命名disk.img
打开终端(cmd)，cd 你的脚本和镜像目录
运行
qemu-img resize disk.img 8G
然后运行
qemu-system-aarch64  -machine type=raspi3b  -m 1024 -dtb dtb.dtb -kernel kernel.img -drive id=hd-root,format=raw,file=disk.img -append "'rw earlycon=pl011,0x3f201000 console=ttyAMA0 loglevel=8 root=/dev/mmcblk0p2 fsck.repair=yes net.ifnames=0 rootwait memtest=1 dwc_otg.fiq_fsm_enable=0"  -serial stdio -netdev user,id=net0,hostfwd=tcp::5555-:22  -usb -device usb-kbd -device usb-tablet  -device usb-net,netdev=net0 
# 树莓派镜像下载
这里提供一个2020年的
https://mirror.tuna.tsinghua.edu.cn/raspberry-pi-os-images/raspios_arm64/images/raspios_arm64-2020-05-28/2020-05-27-raspios-buster-arm64.zip
下载后解压就是img
# 视频教程
https://www.bilibili.com/video/BV195411C7oc
