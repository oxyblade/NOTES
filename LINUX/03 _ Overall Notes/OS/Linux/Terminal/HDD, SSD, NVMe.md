lsblk Просмотр разделов дисков
sudo fdisk -l /dev/sda Просмотр разделов дисков
sudo parted /dev/sda print Просмотр дисков
sudo gdisk -l /dev/sda Просмотр дисков

sudo cfdisk Работа с жесткими дисками
sudo fdisk /dev/sda Разбивка диска на разделы

df -h Сведения о файловой системе
du /home - Show file's size

sudo ncdu / Подсчет размера директорий

======================== S.M.A.R.T. ============================

sudo smartctl

[ INTERNAL ]
sudo smartctl -a /dev/nvme0n1
sudo smartctl -a /dev/sdb

[ USB ]
sudo smartctl -d sat /dev/sda
sudo smartctl -T permissive -a -d scsi /dev/sda

====================== S.M.A.R.T. END ==========================
