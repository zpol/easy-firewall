# easy-firewall
A nice &amp; simple way to manage your iptables firewall
---

Just another way to manage your firewall with less flags/arguments. Specially for novice Linux users
Of course if you need to do more things that scripts actually does, you should use iptables command.

The Easy-Firewall Suite comes with some scripts: 

*iptablesctl*
---
For the moment only works on INPUT chain.

**Firewall Started:** All chains in FILTER table in DROP policy wich means all incomming traffic is dropped ( pings inclusive :). ESTABLISHED and RELATED connections remains active so you are no going to lose your ssh connection for example.
*Example:* iptablesctl start

 Firewall Stopped 	== 	All chains in FILTER table in ACCEPT policy this state is basically
						all incoming traffic is ALLOWED
						Example: iptablesctl stop

 Reload Firewall 	==	This option reloads the firewall configurtion using /etc/firewall.conf file)
						Example: iptablesctl reload

 Save Option 		==	This option saves all actual configuration into /etc/firewall.conf file.
						Example: iptablesctl save

 Load Option 		==	Loads a configuration specified by the filename or path to filename as an argument
 						Example: iptablesctl load /tmp/firewall.conf

 List Option 		==	List the current firewall config
						Example: iptablesctl list
