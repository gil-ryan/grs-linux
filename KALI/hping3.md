# hping3

A simple way to do stress testing is to use the tool _hping3_. You'll basically tell _hping3_  what you want different fields to be set to, and it will create the packet the way you want.

> root@rosebud:~# hping3 --flood -S -p 80 192.168.86.1
