MobaXterm is a freeware that offers **enhanced terminal for Windows with X11 server, SSH clients and other network tools**. The personal home edition of MobaXterm can be downloaded from [http://mobaxterm.mobatek.net/download-home-edition.html](http://mobaxterm.mobatek.net/download-home-edition.html). The free personal edition supports **12 sessions**, which is sufficient for our use.

* Install and launch MobaXterm. When Windos Firewall prompted allow `xwin_mobax` only through private networks, and untick access via Public networks. Do not access these services from open networks.

![MobaXterm_through_firewall](images/mobaxterm_firewall.png)

* In a case of using portable version you need to setup right working directories: Settings => Configuration => General

* For Persistent root directory use MobaXterm install directory

![MobaXterm_portable](images/mobaxterm_portable.png)

* To create an `SSH` session, select `Session` and choose `SSH` in the `Session settings`. 

* Set remote host as `ui-2.hpc.rtu.lv`, tick `Specify user_name` and type your user_name in the box provided. Leave the port to be `22`. Be sure that you mark `Compression` box in `Advanced SSH settings`. This is quite important for slow connections. Click `OK`. 

![MobaXterm_ssh_setup](images/mobaxterm_ssh.png)

* You should now be able to see `ui-2.hpc.rtu.lv(user_name)` in the Sessions tab. Select this session. This should prompt you for your password. This is your RTU HPC password.

* Make setting for X-Server (Settings => Configuration => X-server) like in a picture:

![MobaXterm_X11](images/mobaxterm_X11.png)

* Connect with SSH : Sessions => User Sessions => your’s session name



