# dockerport
An utility to manage VirtualBox port mapping. Designed for boot2docker, but can also work for other vms.

# Dependencies

* Ruby >= 2.0, rbenv installed is recommanded

# Install

* Add current directory to the PATH

# Usage

```
Usage: dockerport COMMAND [OPTIONS] [arg ...]
Commands:
    all                          List all vms
    list  [VM]                   List the specified vm [Default: boot2docker-vm]
    map   PORT | PORT1..PORT2    Map port for the specified vm
    unmap PORT | PORT1..PORT2    Unmap port for the specified vm
```

# Example

```bash
$ dockerport all # List all vms in VirtualBox
boot2docker-vm
Ubuntu
$ dockerport list # List all mapped ports of vm, by default it's boot2docker-vm
name = ssh, protocol = tcp, host ip = 127.0.0.1, host port = 2022, guest ip = , guest port = 22
$ dockerport map -m Ubuntu 8081 # Map 8081 port for Ubuntu
$ dockerport list Ubuntu
name = tcp-port8081, protocol = tcp, host ip = , host port = 8081, guest ip = , guest port = 8081
name = udp-port8081, protocol = udp, host ip = , host port = 8081, guest ip = , guest port = 8081
$ dockerport map --tcp-only -m Ubuntu 8085..8090 # Map TCP ports from 8085 to 8090 for Ubuntu
$ dockerport list Ubuntu
name = tcp-port8081, protocol = tcp, host ip = , host port = 8081, guest ip = , guest port = 8081
name = tcp-port8085, protocol = tcp, host ip = , host port = 8085, guest ip = , guest port = 8085
name = tcp-port8086, protocol = tcp, host ip = , host port = 8086, guest ip = , guest port = 8086
name = tcp-port8087, protocol = tcp, host ip = , host port = 8087, guest ip = , guest port = 8087
name = tcp-port8088, protocol = tcp, host ip = , host port = 8088, guest ip = , guest port = 8088
name = tcp-port8089, protocol = tcp, host ip = , host port = 8089, guest ip = , guest port = 8089
name = tcp-port8090, protocol = tcp, host ip = , host port = 8090, guest ip = , guest port = 8090
name = udp-port8081, protocol = udp, host ip = , host port = 8081, guest ip = , guest port = 8081
$ dockerport unmap --tcp-only -m Ubuntu 8081 8085..8090 # Unmap TCP ports from 8085 to 8090 and 8081 for Ubuntu
$ dockerport list Ubuntu
name = udp-port8081, protocol = udp, host ip = , host port = 8081, guest ip = , guest port = 8081
```
