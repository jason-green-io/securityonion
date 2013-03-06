Security Onion offline install build ISO.txt:
---------------------------------------------

This is my version of how to create a custom install of Security Onion 
using Ubuntu seed files and the Ubuntu server ISO. It was built with Dell R710/R610 in mind
so includes the Dell management software. fluxbox and xorg are also installed to run
sosetup at the console or using an iDRAC remotely.

* so.seed needs to go into /isobuild/preseed

* txt.cfg needs to replace the one in /isobuild/isolinux

geo-update:
-----------

This resides on the server and will will update an offline server's GeoIP for ELSA + Snorby and ip2c for squert.
Just put the geo-update.tar.gz files created gy geo-get in /tmp and run

** if you're running an offline server, you'll also want to change the pulledpork line in /usr/bin/rule-update:

from: /usr/bin/pulledpork.pl -c

to:   /usr/bin/pulledpork.pl -n -c

This will make pulledpork.pl only look in /tmp for the rule sets and not try to download them.
Just drop emerging.rules.tar.gz or whatever in /tmp and run rule-update

geo-get
-------

This resideds on a workstation with internet access and will get the required files for geo-update.

