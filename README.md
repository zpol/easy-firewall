# Easy-firewall
##A nice &amp; simple way to manage your iptables firewall

---


Just another way to manage your firewall in Linux with less flags/arguments. Specially designed for novice Linux users. 
Of course if you need to do more things that scripts actually does, you should use iptables command.

The Easy-Firewall Suite comes with some diferent scripts to cover all main firewall administration tasks: 

##easy-firewall
 
---
**Usage:** easy-firewall allow [port] from [source] to [dest]

easy-firewall uses the IPFW BSD Style. Yes! now you can use in Linux a nice way to "talk" with your firewall. For the moment don't have so many options but you can use it. 

Examples: 

	# easy-firewall allow * from any to me 
	# easy-firewall allow 22 from 192.168.2.32 to 84.66.33.21
	# easy-firewall deny 143 from 217.126.99.233 to me 

##iptablesctl

---
**Usage:** iptablesctl <start|stop|reload|load|save|list>

For the moment only works on INPUT chain.

**Firewall Started:** All chains in FILTER table in DROP policy wich means all incomming traffic is dropped ( pings inclusive :). ESTABLISHED and RELATED connections remains active so you are no going to lose your ssh connection for example.

	# iptablesctl start

**Firewall Stopped:** All chains in FILTER table in ACCEPT policy this state is basically all incoming traffic is ALLOWED

	# iptablesctl stop

**Reload Firewall:** This option reloads the firewall configurtion using /etc/firewall.conf file)

	# iptablesctl reload

**Save Option:** This option saves all actual configuration into /etc/firewall.conf file

	# iptablesctl save

**Load Option:** Loads a configuration specified by the filename or path to filename as an argument

	# iptablesctl load /tmp/firewall.conf

**List Option:** List the current firewall config

	# iptablesctl list



##iptables-add

---
Adds a rule by default into INPUT chain.


**Usage:** iptables-add -n [num] -c [chain] -p [port] -a [action] -s [source] -d [destination]

Examples:

	# iptables-add -n 13 -c OUTPUT -a DROP -p 22 -s 217.126.99.233 -d 80.78.44.56
	# iptables-add -p 44466 -s 7.7.7.7 -d 4.4.4.4 -a ACCEPT
	
Options:

	-n [rule_number]	(1-99999)
	-p [port/service] 	(1-65535)
	-a [action]			(ACCEPT/DROP)
	-s [source]			(IP/host)
	-d [destination]	(IP/host)
	-c [chain]			(INPUT/OUTPUT/FILTER)
	-h Show help

##iptables-remove

---
Remove a rule from INPUT unless you specify another chain.

**Usage:** iptables-remove -n [num] -c [chain]

Examples: 

	# iptables-remove -n 25
	# iptables-remove -n 14 -c INPUT
	
Options: 

	-n [rule_number]	(1-99999)
	-c [chain]			(INPUT/OUTPUT/FILTER)
	

##Installation

There are diferent ways to install Easy-firewall

1. You can clone the entire git repository into /usr/local/bin/ or any other directory in your path. Be sure the files have execution permissions enabled and that's it.
2. Type this in a shell:
	
		# curl http://drlinux.cat/tools/easy-firewall.sh | bash 
	
3. Soon a debian package :P 

Using any of these ways you should be able to type in a console any Easy-firewall command.

Enjoy! ;)


##Requirements
-> iptables installed

-> Be root my friend

.


##Considerations using firewalls and policies
To be honest I think the best way to configure your firewall is to DENY all incomming traffic and open port by port whatever you need to get everything working properly. For this reason Easy-Firewall when enables your firewall it keep the current ESTABLISHED and RELATED connections alive and block all the rest. 

About the firewall policy consider using a DROP policy as Easy-firewall uses instead of using ACCEPT policy and drop port by port...It's not a good practice. Just for your information. It's better to have an access denied because firewall is blocking and fix it, than fix the entire server because is has been hacked. ;) 
 
##Contributions, bugs and more...
Please feel free to send me bugs, bugfixes, or anything related to the app in order to improve it.