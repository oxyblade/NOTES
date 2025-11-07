##### Tracker v2 #####
```
systemctl --user mask tracker-store.service tracker-miner-fs.service tracker-miner-rss.service tracker-extract.service tracker-miner-apps.service tracker-writeback.service
```

```
tracker reset --hard
```

reboot

```
tracker status
tracker daemon
```

##### Tracker v3 #####
```
systemctl --user mask tracker-extract-3.service tracker-miner-fs-3.service tracker-miner-rss-3.service tracker-writeback-3.service tracker-xdg-portal-3.service tracker-miner-fs-control-3.service
```

```
tracker3 reset -s -r
```

reboot

```
tracker3 status
tracker3 daemon
```

___

Undo this change and enable Tracker back:

##### Tracker v2 #####
```
systemctl --user unmask tracker-store.service tracker-miner-fs.service tracker-miner-rss.service tracker-extract.service tracker-miner-apps.service tracker-writeback.service
```

##### Tracker v3 #####
```
systemctl --user unmask tracker-extract-3.service tracker-miner-fs-3.service tracker-miner-rss-3.service tracker-writeback-3.service tracker-xdg-portal-3.service tracker-miner-fs-control-3.service
```

reboot

Tracker v2
```
tracker status
tracker daemon
```

Tracker v2
```
tracker3 status
tracker3 daemon
```