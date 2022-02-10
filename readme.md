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

