# gl-ar300m-wifipineapple
Wifi PIneapple for GL-AR300M


1. Flash stock firmware (openwrt-ar300m-ubi-2.264.img) with uboot to nand
2. boot it
3. on "firmware upgrade" page use openwrt-ar71xx-nand-gl-ar300m-squashfs-sysupgrade.tar, set "keep settings" to NONE
4. wait
5. connect to web interface and setup your password
6. ssh root@172.16.42.1
7. ~~edit /pineapple/api/pineapple.php~~
```php
function getDevice()
{
	$data = file_get_contents('/proc/cpuinfo');
	if (preg_match('/NANO/', $data)) {
		return 'nano';
	} elseif (preg_match('/TETRA/', $data)) {
		return 'tetra';
	}
	 change this>>>>>>>return 'nano';
}
```
8. connect to internet


to install ettercap:

1. upload libpcap_1.8.1-1_ar71xx.ipk to your device via scp
2. install it - opkg install libpcap_1.8.1-1_ar71xx.ipk
3. install ettercap - opkg install ettercap --force-depends


bugs: 
LAN and WAN interfaces are misplaced 
