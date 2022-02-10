# Test to start ecmc as a service

## Preparations 
Need to install procServ

Also need todo the follwoing subdirs to this dir:

* run
* run/info
* procServ_Dir


Move mcu1025.script to /etc/systemd/system


## Check paths
Check all paths in:
* mcu1025.service 
* env.sh (that sources the environment)

## Control service

start service with:
```
systemctl start mcu1025
```

stop service with:
```
systemctl stop	mcu1025
```

## Logs
In the procServ.log file you can see the iocsh output.
```
@@@ Restarting child "mcu1025"
@@@    (as /epics/base-7.0.5/require/3.4.1/bin/iocsh.bash)
@@@ The PID of new child "mcu1025" is: 29271
@@@ @@@ @@@ @@@ @@@
Loading environment variables from /home/anderssandstrom/sources/test_service/env.sh

Set the ESS EPICS Environment as follows:
THIS Source NAME    : setE3Env.bash
THIS Source PATH    : /epics/base-7.0.5/require/3.4.1/bin
EPICS_BASE          : /epics/base-7.0.5
EPICS_HOST_ARCH     : linux-x86_64
E3_REQUIRE_LOCATION : /epics/base-7.0.5/require/3.4.1
PATH                : /epics/base-7.0.5/require/3.4.1/bin:/epics/base-7.0.5/bin/linux-x86_64:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin
LD_LIBRARY_PATH     : /epics/base-7.0.5/lib/linux-x86_64:/epics/base-7.0.5/require/3.4.1/lib/linux-x86_64

Enjoy E3!
registerChannelProviderLocal firstTime true
#
# Start at "2022-W06-Feb09-1643-44-CET"
#
# Version information:
...
...
```

## Some usefull comamnds
```

  328  2022-02-09 16:42:49 sudo systemctl daemon-reload
  329  2022-02-09 16:42:52 sudo systemctl start mcu1025.service
  330  2022-02-09 16:42:55 sudo journalctl -xe
  331  2022-02-09 16:43:41 sudo systemctl stop mcu1025.service
  332  2022-02-09 16:43:43 sudo systemctl start mcu1025.service
```

## Troubleshooting

Seems most of the issues I was experiencing was releted to user rights.
I needed to remove iocuser and iocgroup so maybe ecmc is not started up correct (with correct prio and memlock)

Need to look into how to set up user and make it work

