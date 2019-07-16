


<br><b>High level Diagram of Lab Setup   

![title](img/FI-NodeDiagramHighLevelVIew.png)

<b>Login to OpenStack Server   </b>


<b>ssh backflip@131.234.26.10   </b>
 


<b>ssh fi@192.168.122.10   </b>



<br>


<b>import openstack related information to run command from cli</b>

fi@fi:~$ source /opt/stack/devstack/accrc/admin/admin  

![VMs Information ( private ips,floating ips )](img/vms-info.png)

<br><b>OpenStack Dashboard:  </b>
http://131.234.26.10   
    <br>

![VMs Instance from Dashboard](img/instance-from-gui.png)

<b> Login to VNFs:

root@fi:~# cd /root  
root@fi:~# ssh -i key1.pri ubuntu@172.24.4.100


root@fi:~# cd /root  
root@fi:~# ssh -i host1.pri ubuntu@172.24.4.190  



root@fi:~# cd /root  
root@fi:~# ssh -i host1.pri ubuntu@172.24.4.209  

<br>
<b> Bridge Details:


![Bridge Setup](img/fi-bridge-setup.png)

root@sf1:~# cat bridge.sh
#!/bin/bash  
brctl addbr br0  
ifconfig ens6 0.0.0.0 promisc  
ifconfig ens7 0.0.0.0 promisc  
#brctl addif br0 ens6  
#brctl addif br0 ens7  
brctl addif br0 ens6 ens7  
ip addr add 192.168.210.20/24 dev br0  
ip addr add 192.168.220.20/24 dev br0  
ip link set dev br0 up  


<br>

<b>Issue at this moment: </b>


1. not able to ping host1 to host2 or vice versa

2. from VNF(sf1) we can ping either HOST1 or HOST2

3. Need to work on bridge setup part as it's not allowing bidrectional connection





```python

```
