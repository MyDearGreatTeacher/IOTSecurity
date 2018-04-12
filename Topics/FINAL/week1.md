
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

### 安裝 Mutillidae

```
cd /var/www/html
sudo wget https://jaist.dl.sourceforge.net/project/mutillidae/mutillidae-project/LATEST-mutillidae-2.6.60.zip

sudo vim mutillidae/classes/MySQLHandler.php
------------------------------------------------------
static public $mMySQLDatabaseUsername = root;
static public $mMySQLDatabasePassword = XXXXXXXXXX;
------------------------------------------------------

sudo rm -rf mutillidae/.htaccess


```
### 安裝 bwapp

### 安裝 NodeGoat 

```
raspberry pi 要設定當前時間
sudo date -s "2018/03/29 22:38:32"
```

```
sudo apt-get update
sudo apt-get install nodejs
sudo apt-get install npm
sudo apt install nodejs-legacy
```

```
git clone https://github.com/OWASP/NodeGoat.git
cd NodeGoat
npm install
```
啟動NodeGoat==>npm start
```
Admin Account - u:admin p:Admin_123
User Accounts (u:user1 p:User1_123), (u:user2 p:User2_123)
New users can also be added using the sign-up page.
```

打開瀏覽器 http://localhost:4000/



# 安裝docker
```
sudo apt install docker.io
```
docker -v

Docker version 1.13.1, build 092cba3
```

 sudo docker --help
```
Usage:  docker COMMAND

A self-sufficient runtime for containers

Options:
      --config string      Location of client config files (default "/home/ksu/.docker")
  -D, --debug              Enable debug mode
      --help               Print usage
  -H, --host list          Daemon socket(s) to connect to (default [])
  -l, --log-level string   Set the logging level ("debug", "info", "warn", "error", "fatal") (default "info")
      --tls                Use TLS; implied by --tlsverify
      --tlscacert string   Trust certs signed only by this CA (default "/home/ksu/.docker/ca.pem")
      --tlscert string     Path to TLS certificate file (default "/home/ksu/.docker/cert.pem")
      --tlskey string      Path to TLS key file (default "/home/ksu/.docker/key.pem")
      --tlsverify          Use TLS and verify the remote
  -v, --version            Print version information and quit

Management Commands:
  container   Manage containers
  image       Manage images
  network     Manage networks
  node        Manage Swarm nodes
  plugin      Manage plugins
  secret      Manage Docker secrets
  service     Manage services
  stack       Manage Docker stacks
  swarm       Manage Swarm
  system      Manage Docker
  volume      Manage volumes

Commands:
  attach      Attach to a running container
  build       Build an image from a Dockerfile
  commit      Create a new image from a container's changes
  cp          Copy files/folders between a container and the local filesystem
  create      Create a new container
  diff        Inspect changes on a container's filesystem
  events      Get real time events from the server
  exec        Run a command in a running container
  export      Export a container's filesystem as a tar archive
  history     Show the history of an image
  images      List images
  import      Import the contents from a tarball to create a filesystem image
  info        Display system-wide information
  inspect     Return low-level information on Docker objects
  kill        Kill one or more running containers
  load        Load an image from a tar archive or STDIN
  login       Log in to a Docker registry
  logout      Log out from a Docker registry
  logs        Fetch the logs of a container
  pause       Pause all processes within one or more containers
  port        List port mappings or a specific mapping for the container
  ps          List containers
  pull        Pull an image or a repository from a registry
  push        Push an image or a repository to a registry
  rename      Rename a container
  restart     Restart one or more containers
  rm          Remove one or more containers
  rmi         Remove one or more images
  run         Run a command in a new container
  save        Save one or more images to a tar archive (streamed to STDOUT by default)
  search      Search the Docker Hub for images
  start       Start one or more stopped containers
  stats       Display a live stream of container(s) resource usage statistics
  stop        Stop one or more running containers
  tag         Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE
  top         Display the running processes of a container
  unpause     Unpause all processes within one or more containers
  update      Update configuration of one or more containers
  version     Show the Docker version information
  wait        Block until one or more containers stop, then print their exit codes

Run 'docker COMMAND --help' for more information on a command.
```
