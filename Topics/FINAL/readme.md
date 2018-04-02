
# 期末專案:物聯網設備的攻擊實測

## 建置dvwa測試平台在Raspberry PI 3 websecurity@IOT devices

### [1]下載
```
你可你裝裝其他作業系統玩玩看
訪問樹莓派官網https://www.raspberrypi.org/

在樹莓派作業系統的下載頁面選擇你要的:
https://www.raspberrypi.org/downloads/

本次練習:下載UbuntuMATE系統鏡像。
點擊Ubuntu MATE系統圖標後會跳轉到下載頁面https://ubuntu-mate.org/raspberry-pi/。
下載:https://ubuntu-mate.org/raspberry-pi/
```
### [2]安裝{1}:使用Windows的Win32DiskImager
```
下載Win32DiskImager:  https://sourceforge.net/projects/win32diskimager/
安裝Win32DiskImager:

使用Windows的Win32DiskImager寫入Ubuntu
Insert the SD card into your SD card reader. 
You can use the SD card slot if you have one, or an SD adapter in a USB port. 
Note the drive letter assigned to the SD card. You can see the drive letter 
in the left hand column of Windows Explorer, for example G:

Download the Win32DiskImager utility from the Sourceforge Project page as an installer file, 
and run it to install the software.
Run the Win32DiskImager utility from your desktop or menu.
```
### [2]安裝{2}:使用Windows的Win32DiskImager安裝Ubuntu MATE
```
Select the image file you extracted earlier.
In the device box, select the drive letter of the SD card. Be careful to select the correct drive: 
if you choose the wrong drive you could destroy the data on your computer's hard disk! 
If you are using an SD card slot in your computer, and can't see the drive in the Win32DiskImager window, 
try using an external SD adapter.

Click 'Write' and wait for the write to complete.

Exit the imager and eject the SD card.
https://www.youtube.com/watch?v=EBBwymU9HOM


sudo apt-get install gddrescue xz-utils
unxz ubuntu-mate-16.04.2-desktop-armhf-raspberry-pi.img.xz
sudo ddrescue -D --force ubuntu-mate-16.04.2-desktop-armhf-raspberry-pi.img /dev/sdx
```
### [3]安裝{3}:apache+Mysql+PHP

```
sudo apt-get install apache2 php libapache2-mod-php php-curl php-mcrypt php-mbstring phpunit php-gd -y
sudo apt-get install mysql-server php-mysqli -y
sudo service apache2 restart
```
### [4]安裝{4}:安裝DVWA
```
cd /var/www/html
git clone https://github.com/ethicalhack3r/DVWA.git
cp DVWA/config/config.inc.php.dist DVWA/config/config.inc.php

修改設定檔:vim DVWA/config/config.inc.php
```

```
<?php

# If you are having problems connecting to the MySQL database and all of the va$
# try changing the 'db_server' variable from localhost to 127.0.0.1. Fixes a pr$
#   Thanks to @digininja for the fix.

# Database management system to use
$DBMS = 'MySQL';
#$DBMS = 'PGSQL'; // Currently disabled

# Database variables
#   WARNING: The database specified under db_database WILL BE ENTIRELY DELETED $
#   Please use a database dedicated to DVWA.
#
# If you are using MariaDB then you cannot use root, you must use create a dedi$
#   See README.md for more information on this.
$_DVWA = array();
$_DVWA[ 'db_server' ]   = '127.0.0.1';
$_DVWA[ 'db_database' ] = 'dvwa';

# Only used with PostgreSQL/PGSQL database selection.
$_DVWA[ 'db_port '] = '5432';

# ReCAPTCHA settings
#   Used for the 'Insecure CAPTCHA' module
#   You'll need to generate your own keys at: https://www.google.com/recaptcha/$
# $_DVWA[ 'recaptcha_public_key' ]  = '';
# $_DVWA[ 'recaptcha_private_key' ] = '';

$_DVWA[ 'recaptcha_public_key' ] = '6LfQNCYTAAAAALx0oAwtLHJlzNHXTKLl2UZjQjw-';
$_DVWA[ 'recaptcha_private_key' ] = '6LfQNCYTAAAAAHnvqCzw2lG95FD-RfomKHWf7Zob';


# Default security level
#   Default value for the secuirty level with each session.
#   The default is 'impossible'. You may wish to set this to either 'low', 'med$
# $_DVWA[ 'default_security_level' ] = 'impossible';  這是你打不進去的關卡
$_DVWA[ 'default_security_level' ] = 'low';

# Default PHPIDS status 預設PHIDS(入侵偵測系統)
#   PHPIDS status with each session.
#   The default is 'disabled'. You can set this to be either 'enabled' or 'disa$
$_DVWA[ 'default_phpids_level' ] = 'disabled';

# Verbose PHPIDS messages
#   Enabling this will show why the WAF blocked the request on the blocked requ$
#   The default is 'disabled'. You can set this to be either 'true' or 'false'.
$_DVWA[ 'default_phpids_verbose' ] = 'false';
?>
```
```
註記:特別注意單引號''
-----------------------------------------------------
$_DVWA[ 'db_user' ] = 'root';
$_DVWA[ 'db_password' ] = 'xxxxxxxxxx';


$_DVWA[ 'recaptcha_public_key' ] = 'xxxxxxxxxxxxxx';
$_DVWA[ 'recaptcha_private_key' ] = 'xxxxxxxxxxxxx';

$_DVWA[ 'default_security_level' ] = ‘low';
-----------------------------------------------------

sudo chmod +777  /var/www/html/DVWA/hackable/uploads/
sudo chmod  +777 /var/www/html/DVWA/external/phpids/0.6/lib/IDS/tmp/phpids_log.txt

https://www.digitalocean.com/community/tutorials/how-to-set-up-mod_security-with-apache-on-debian-ubuntu
```
