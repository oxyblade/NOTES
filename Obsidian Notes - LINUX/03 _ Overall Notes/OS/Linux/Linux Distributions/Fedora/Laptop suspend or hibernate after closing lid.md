1. Show location of swap partition:

```
swapon -s
```

2. Edit grub file:

```
sudo nano /etc/default/grub
```

3. Add or edit resume value in grub file (GRUB_CMDLINE_LINUX):

```
resume=(/location/of/swap/partition)
```

4. Regenerate the grub file:

```
sudo grub2-mkconfig --output=/boot/grub2/grub.cfg
```