Check size of directories and files
du -sh * | sort -h
du -h | sort -h

`sudo find /media/WD/ -type d -exec chmod 755 {} \;    => Change DIRECTORIES Permissions`
`sudo find /media/WD/ -type f -exec chmod 644 {} \;    => Change FILES Permissions`
`sudo find . -type d -exec chmod 755 {}; && find . -type f -exec chmod 644 {};`

find -printf "%P\n" > listing.xlsx
find . -type f \( -name "*.docx" -o -name "*.doc" -o -name "*.rtf" -o -name "*.odt" -o -name "*.pptx" -o -name "*.ppt" -o -name "*.xlsx" -o -name "*.xls" -o -name "*.txt" -o -name "*.png" -o -name "*.jpg" -o -name "*.jpeg" \) -execdir soffice --headless --convert-to pdf "{}" \;

Make links between files (TARGET (From) -> LINK_NAME (To)):
ln -s /opt/phpstorm/bin/phpstorm.sh /usr/local/bin/phpstorm

Создать поддерево каталогов:
mkdir -p tmpdir/temp/dir

Копирование:
Копирование файла: sudo cp /dir/file /newdir/
Копирование каталога: sudo cp /home/dir /usr/local/
Копирование содержимого каталога: sudo cp -rp /dir/* /to/dir/

Перемещение каталога:
sudo mv fromPath/ toPath/

Перемещение файлов:
sudo mv fromPath/testfile toPath/testfile
sudo mv ~/Downloads/*.mp3 ~/Music/

Rename Directory or File:
mv oldnamefile1 newnamefile1
mv oldDir/ newDir

Удаление:
Удаление файла в текущей директории: rm filename
Удаление директории и содержащихся в ней файлов и подпапок: rm -r foldername
Удаление всех файлов в директории: rm /path/to/folder/*
Удаление файла размещенного за пределами текущей директории: rm /path/to/folder/filename
Удаление пустой директории: rmdir foldername
Если удаления файла требует привилегий суперпользователя: sudo rm filename
Если удаления директории требует привилегий суперпользователя: sudo rm -r foldername

find /catalog_here -type f -printf '%TY-%Tm-%Td %TT %p\n' | sort -r Поиск и сортировка всех файлов
в порядке убывания по числу последнего редактирования

wc - Посчет количества строк или слов в тексте файлов
grep -inr "some_text" /home/andrew/data/documents/ Поиск ключевых слов в файлах

ls -la
ls -a | sort 								-- Output only file names with extensions
ls | rev | cut -d . -f 2- | rev | sort 		-- Output only file names without extensions

LibreOffice batch convert files:
alias qq-libreoffice-convertall-to-pdf='soffice --headless --convert-to pdf --outdir /mnt/WD/Downloads__WD/06_Temp/ *.docx *.doc *.rtf *.odt *.pptx *.ppt'
alias qq-libreoffice-convert-docx-to-pdf='soffice --headless --convert-to pdf --outdir /mnt/WD/Downloads__WD/06_Temp/ *.docx'
alias qq-libreoffice-convert-doc-to-pdf='soffice --headless --convert-to pdf --outdir /mnt/WD/Downloads__WD/06_Temp/ *.doc'
alias qq-libreoffice-convert-rtf-to-pdf='soffice --headless --convert-to pdf --outdir /mnt/WD/Downloads__WD/06_Temp/ *.rtf'
alias qq-libreoffice-convert-odt-to-pdf='soffice --headless --convert-to pdf --outdir /mnt/WD/Downloads__WD/06_Temp/ *.odt'
alias qq-libreoffice-convert-pptx-to-pdf='soffice --headless --convert-to pdf --outdir /mnt/WD/Downloads__WD/06_Temp/ *.pptx'
alias qq-libreoffice-convert-ppt-to-pdf='soffice --headless --convert-to pdf --outdir /mnt/WD/Downloads__WD/06_Temp/ *.ppt'

qq-libreoffice-convert-docx-to-pdf
qq-libreoffice-convert-doc-to-pdf
qq-libreoffice-convert-rtf-to-pdf
qq-libreoffice-convert-odt-to-pdf
qq-libreoffice-convert-pptx-to-pdf
qq-libreoffice-convert-ppt-to-pdf
