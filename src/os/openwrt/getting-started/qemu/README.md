# OpenWrt setup for QEMU

1. Download qemu-system-mips
```
sudo apt install qemu-system-mips
```
2. Configure OpenWrt for qemu
    1. Open configuration menu
    ```
    make menuconfig
    ```
    2. Specify target system as MIPS by selecting `Target System -> MIPS Malta CoreLV board (qemu)`
    3. Specify image format as ext4 by selecting `Target Images -> ext4`
3. Compile
```
make -j$(nproc)
```
4. Copy generated filesystem and image to qemu run directory
```
mkdir qemu
cp bin/targets/malta/le/openwrt-malta-le-rootfs-ext4.img qemu
cp bin/targets/malta/le/openwrt-malta-le-vmlinux.elf qemu
```
5. Run qemu
```
cd qemu
sudo qemu-system-mipsel -M malta -hda openwrt-malta-le-rootfs-ext4.img -kernel openwrt-malta-le-vmlinux.elf -nographic -append "root=/dev/sda console=ttyS0"
```