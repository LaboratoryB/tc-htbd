GPLv2
THIS IS A TC (TRAFFIC CONTROL) MANAGMENT SCRIPT.
IT CAN BE USED AS A DAEMON LIKE SCRIPT, WHILE
FUNCTIONAL, IT IS NOT A FINISHED PACKAGE.

CURRENTLY SCRIPT IS SET TO READ CONFIGURATION 
DETAILS FROM HERE: /etc/sysconfig/tc-htb

THE FORMAT OF "/etc/sysconfig/tc-htb" IS:
<OUTSIDE IP> <INSIDE IP> <DOWNLOAD> <UPLOAD> <PRIORITY>


SOMETHING LIKE THIS SHOULD HACK IT INTO BOOTABLE ON CENTOS:
$ cp tc-htbd /etc/init.d/
$ ln -s /etc/init.d/tc-htbd /etc/rc.d/rc3.d/S90tc-htbd
$ ln -s /etc/init.d/tc-htbd /etc/rc.d/rc5.d/S90tc-htbd

(Or you could throw it in rc.local, call the script with
"start", I won't tell anyone; need to package this up to 
make it right; I'll proably at least put a spec file 
together if I go much farther with this-not sure with
.debs, but tc is kernel level, so should work fine with
a few ".conf" tweaks)


DEVEL NOTES:
NEEDS WORK TO SPLIT OUT INTO A PROPER PACAKGE AND
CREATE A PROPER DAEMON.  IF I CONTINUE WORK ON THIS,
I'LL WANT TO ADD A MORE PROGRAMATIC APPROACH, 
PARTICULARLIY WITH CONFIGURABLE VARIABLES FOR THE 
CLASSES SETUP.  I THINK THIS SHOULD ALLOW DYNAMIC
CONFIGURATION UP TO $CEIL WITH A SIMPLE ".conf" FILE
