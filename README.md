# gfwdns
一个针对 GFW 的 DNS 污染而设计的反制工具，它的逻辑基于一个并不可靠的规律，即“GFW制造的 DNS 污染所返回的错误 IP 地址均在墙外”。

#为什么使用
gfwdns 可以让您在避免受到 GFW 污染的同时享受墙内 DNS 提供的 CDN 加速服务，同时避免访问墙内网站设置在墙外的镜像服务器以节约带宽。

#参数
```
--gfwdns-dns-white=白名单 DNS 的 IP 地址
--gfwdns-dns-black=黑名单 DNS 的 IP 地址
```
#调试示例
```
/usr/sbin/dnsmasq --no-daemon --log-queries --conf-file=/var/etc/dnsmasq.conf --gfwdns-dns-white=127.0.0.1#5353 --server=127.0.0.1#5353 --server=114.114.114.114
```  

#平台
目前 gfwdns 仅提供在 OpenWrt SDK 环境下的编译文件，如果您愿意并能够让它工作在更多的平台下，欢迎提交补丁。

#编译与使用
下载后放入 OpenWrt SDK 根目录并执行 make 命令，即可启动编译过程。软件运行过程中需要 GeoIP.dat 文件，请在下载并解压后将其放入"/usr/share/GeoIP/"目录即可。
```
wget -N http://geolite.maxmind.com/download/geoip/database/GeoLiteCountry/GeoIP.dat.gz
```
