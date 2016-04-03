1:
Q:ping通但是ssh不通。
A：目的主机的防火墙开启。service iptables stop  //关闭防火墙
   service sshd start //启动sshd服务。
  ssh 是通过22端口L4传输层。 ping是ICMP协议L4传输层。
