## anonsurf 

ParrotSec's anonsurf and stealth, ported to work with Kali Linux / Termux.

## How to use this repo

This repo contains the sources of both the anonsurf and pandora packages from ParrotSec combined into one.

Modifications have been made to use the DNS servers of Private Internet Access (instead of FrozenDNS), and fixes for users who don't use the resolvconf application. I have removed some functionality such as the gui and iceweasel in ram.

This repo can be compiled into a deb package to correctly install it on a Kali system.

The easiest way to get this working is to just run the installer. See the installation section for further info.

NOTE: This may work with any debian/ubuntu system, but this has only been tested to work on a kali-rolling amd64 system

## Usage
### Pandora
Pandora automatically overwrites the RAM when the system is shutting down. Pandora can also be ran manually:
```bash
pandora bomb
```

NOTE: This will clear the entire system cache, including active SSH tunnels or sessions.

### anonsurf usage
Anonsurf will anonymize the entire system under TOR using IPTables. It will also allow you to start and stop i2p as well.

NOTE: DO NOT run this as ```service anonsurf $COMMAND```. Run this as ```anonsurf $COMMAND```

```bash
Usage:
 anonsurf {start|stop|restart|change|status}

 start - Start system-wide anonymous
          tunneling under TOR proxy through iptables
 stop - Reset original iptables settings
          and return to clear navigation
 restart - Combines "stop" and "start" options
 change - Changes identity restarting TOR 
 status - Check if AnonSurf is working properly
----[ I2P related features ]----
 starti2p - Start i2p services
 stopi2p - Stop i2p services
```

## Installation
This package comes with an installer that makes things extremely easy:

```bash
git clone https://github.com/keralahacker/anonsurf
cd anonsurf && chmod +x *
./installer.sh
```
### Example in kali Linux 
```
kali@kali:~$ sudo anonsurf start
[sudo] password for kali: 
 * killing dangerous applications
 * cleaning some dangerous cache elements
[ i ] Stopping IPv6 services:


[ i ] Starting anonymous mode:

 * Tor is not running!  starting it  for you

 * Modified resolv.conf to use Tor and Private Internet Access DNS
 * All traffic was redirected through Tor

[ i ] You are under AnonSurf tunnel


kali@kali:~$ sudo anonsurf status
? tor.service - Anonymizing overlay network for TCP (multi-instance-master)
     Loaded: loaded (/lib/systemd/system/tor.service; disabled; vendor preset: disabled)
     Active: active (exited) since Wed 2020-12-16 18:31:22 UTC; 9s ago
    Process: 1867 ExecStart=/bin/true (code=exited, status=0/SUCCESS)
   Main PID: 1867 (code=exited, status=0/SUCCESS)

Dec 16 18:31:22 kali systemd[1]: Starting Anonymizing overlay network for TCP (multi-instance-master)...
Dec 16 18:31:22 kali systemd[1]: Finished Anonymizing overlay network for TCP (multi-instance-master).

kali@kali:~$ sudo anonsurf myip

My ip is:

51.77.148.119

----------------------------------------------------------------------

kali@kali:~$ 
```
Once the installer is complete, you will be able to use both the anonsurf and pandora modules.
