---
title: Setup Shadowsocks server on Ubuntu
date: 2017-10-29 20:49:10
---

Thanks to the great great GFW, recently I have difficulty in using foreign web services. Since VPN applications are expensive and not so reliable, I decide to use Shadowsocks server to reach the outside world. Besides, Amazon Web Service (AWS) is free to use for 12 months, so it is not a tough decision for me to choose AWS as my web service.

## Amazon Web Service
First of all, go to [aws.amazon.com](aws.amazon.com) to register your cloud service, then go to **AWS Management Console** and select **EC2** service. There are multiple regions of EC2 available for you to choose. Personally, I choose Tokyo service because Tokyo is the closest service to Shanghai. Thus it is the most stable service and fast service. After registering, one can simply create an instance which would later be used as a ladder.

The most important thing in creating an instance is to download and keep your **key file** (*.pem) safely, which would be used to connect the instance.

![image](/images/2017-10-29-setup-shadowsocks-server-on-ubuntu/awsins.png)

After that, you can connect to the instance by simply following the instructions:

![image](/images/2017-10-29-setup-shadowsocks-server-on-ubuntu/awsconn.png)

A successful connection through SSH should be like this:

![image](/images/2017-10-29-setup-shadowsocks-server-on-ubuntu/awslog.png)

Next, you should install Shadowsocks on the instance:

    sudo yum install -y python-setuptools
    sudo easy_install pip
    sudo pip install shadowsocks

And configure Shadowsocks server:

    mkdir /etc/shadowsocks
    sudo vim /etc/shadowsocks/config.json

![image](/images/2017-10-29-setup-shadowsocks-server-on-ubuntu/ssconfig.png)

Run & Stop Shadowsocks server:

    sudo ssserver -c /etc/shadowsocks/config.json -d start
    sudo ssserver -c /etc/shadowsocks/config.json -d stop
    sudo ssserver -c /etc/shadowsocks/config.json -d restart

Note that you need to do some changes in the **Security Group**, specifically, to add an inbound rule. This means that one can connect instance through the port, otherwise, you would be blocked out and never connect this instance.

![image](/images/2017-10-29-setup-shadowsocks-server-on-ubuntu/inbound.png)

## Ubuntu
First of all, install the Shadowsocks-GUI from [github.com/shadowsocks/shadowsocks-qt5](https://github.com/shadowsocks/shadowsocks-qt5), which is a cross-platform Shadowsocks client. Thank you guys.

Second, manually add a connection profile. Enter the corresponding information as specified in the above /etc/shadowsocks.json file on your server. Once done, click OK to save the profile.

![image](/images/2017-10-29-setup-shadowsocks-server-on-ubuntu/ssqt1.png)

Last, try connecting the Shadowsocks server, a successful connection should be like this:

![image](/images/2017-10-29-setup-shadowsocks-server-on-ubuntu/ssqt0.png)

**Important!** One must edit the Ubuntu system network setting to let the proxy work.

    System Settings => Network => Network proxy, Method => Manual    
    HTTP Proxy => empty 8080, Socks Host => 127.0.0.1 1080
![image](/images/2017-10-29-setup-shadowsocks-server-on-ubuntu/ubuntunw.png)

## Here we go, Come on!

![image](/images/2017-10-29-setup-shadowsocks-server-on-ubuntu/gg.png)

Actually, the GFW blocks numerous harmful things like porn for Chinese netizens, which is benefical for the clean and healthy Internet environment. However, in the long run, GFW will disturb Chinese netizens from acknowledging global events and affairs, and most importantly, keep the regime safe and solid. All in all, We have no choice, but we have tools to make us powerful!
