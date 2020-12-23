# Fragroute

_Fragroute_ was written a long time ago by _Dug Song_. It takes a series of rules and applies them to any packet that it sees destined to an IP address you specify.

With _fragroute_ you can truly manipulate network packets.

```
ip_chaff dup 7
ip_frag 64 new
drop random 33
dup random 40
order random
print
```

In an IP packet, the __IP identification__  field binds all fragments together, so all fragments with the same IP identification field belong to the same packet. The fragment offset field indicates where the fragment belongs in the overall scheme of the packet.

Ideally you'll have something like 0-1200 bytes in one packet fragment and the offset in the second fragment would start at 1201, indicating that it's the next one to be put back together. You may get several more of roughly the same size and the network stack on the receiving end puts them all together like squares in a quilt until the quilt is whole.

