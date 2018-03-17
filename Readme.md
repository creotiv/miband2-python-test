# Mi Band 2 python test

Playing around with the [**Mi Band 2**](http://www.mi.com/en/miband2/) and Linux.

- [Mi Band 2, Part 1: Authentication](https://leojrfs.github.io/writing/miband2-part1-auth/)

![demo](/demo.png)

## Setting up

First, it's best to unbind your Mi Band 2 from MiFit App.  
You should be able to bind it back again, but no guaranee here ;)

```sh
pip2 install  bluepy --user
```

On the first run, you need to init your device with a new key:
```sh
miband2-auth.py YOUR_MAC --init
```

After that, you can run some sample tests:
```sh
miband2-auth.py YOUR_MAC --notify
miband2-auth.py YOUR_MAC --heart
```

## Cheatsheet

List all visible BLE devices to find out the MAC address:
```sh
sudo hcitool lescan
```

To list all descriptors of a device:
```sh
sudo gatttool -b YOUR_MAC -I -t random
> connect
> char-desc
```

Sometimes, BLE stack might fail, and the reset is needed:

```sh
sudo hciconfig hci0 reset
```
