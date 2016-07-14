#                       FastDFS Installation manual

![](https://github.com/lixwlixw/fastdfs-install/blob/master/pic1.png)
#####Tracker (10.1.130.153) Nginx Load balancing + cache
![](https://github.com/lixwlixw/fastdfs-install/blob/master/pic2.png) ![](https://github.com/lixwlixw/fastdfs-install/blob/master/pic2.png)
##### Group1 Storage x 2#######group2 Storage x 2 
#####10.1.130.152 10.1.130.154####  10.1.130.123 10.1.130.124

##1.Install the compiler tools and libfastcommon
###<br />All servers:<br />
<br />`yum -y groupinstall 'Development Tools' && yum -y install wget`<br />
<br />`wget https://github.com/happyfish100/libfastcommon/archive/master.zip`<br />
<br />`unzip master.zip`<br />
<br />`cd libfastcommon-master`<br />
<br />`./make.sh`<br />
<br />`./make.sh install`<br />
##2.Install FastDFS
###<br />All servers:<br />
<br />`wget https://github.com/happyfish100/fastdfs/archive/V5.05.tar.gz`<br />
<br />`tar -zxvf V5.05.tar.gz`<br />
<br />`cd fastdfs-5.05/`<br />
<br />`./make.sh`<br />
<br />`./make.sh install`<br />
###<br />Tracker:<br />
<br />`mv /etc/fdfs/tracker.conf.sample  /etc/fdfs/tracker.conf`<br />
<br />`Vi  /etc/fdfs/tracker.conf`<br />
![](https://github.com/lixwlixw/fastdfs-install/blob/master/pic4.png)

<br />`iptables -I INPUT -p tcp -m state --state NEW -m tcp --dport 22122 -j ACCEPT`<br />
<br />`fdfs_trackerd /etc/fdfs/tracker.conf start`<br />
###<br />Storage:<br />
<br />`mv /etc/fdfs/storage.conf.sample  /etc/fdfs/storage.conf `<br />
<br />`Vi /etc/fdfs/storage.conf`<br />
![](https://github.com/lixwlixw/fastdfs-install/blob/master/pic5.png)

![](https://github.com/lixwlixw/fastdfs-install/blob/master/pic6.png)

![](https://github.com/lixwlixw/fastdfs-install/blob/master/pic9.png)

![](https://github.com/lixwlixw/fastdfs-install/blob/master/pic7.png)
![](https://github.com/lixwlixw/fastdfs-install/blob/master/pic8.png)
![](https://github.com/lixwlixw/fastdfs-install/blob/master/pic9.png)
<br />`iptables -I INPUT -p tcp -m state --state NEW -m tcp --dport 23000 -j ACCEPT`<br />
<br />`fdfs_storaged /etc/fdfs/storage.conf`<br />


