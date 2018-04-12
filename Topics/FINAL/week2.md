# 期末專案:物聯網設備的攻擊實測

## 建置dvwa測試平台在Raspberry PI 3 websecurity@IOT devices

### 漏洞測試
```
測試


```

### 檢視apache web server的log檔

```
/var/log/apache2
access.log       
error.log       
modsec_audit.log


```

cat access.log

```
192.168.2.50 - - [12/Apr/2018:00:12:14 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 530 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:12:14 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:12:14 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:22:19 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 530 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:22:19 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:22:19 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:26:39 +0800] "GET /1 HTTP/1.1" 404 494 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:26:40 +0800] "GET /1 HTTP/1.1" 404 493 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:26:42 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:26:42 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:27:37 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 530 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:27:37 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:30:24 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 530 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:30:25 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 530 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:30:25 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:33:12 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 530 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:33:12 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:33:32 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 530 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:33:32 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:33:44 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 530 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:33:45 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:33:47 +0800] "GET /DVWA/vulnerabilities/sqli/ HTTP/1.1" 200 1805 "http://192.168.2.61/DVWA/vulnerabilities/captcha/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:33:47 +0800] "GET /DVWA/favicon.ico HTTP/1.1" 200 1706 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:33:48 +0800] "GET /DVWA/vulnerabilities/sqli/ HTTP/1.1" 200 1805 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:33:50 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:35:08 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 530 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:35:08 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:35:09 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:39:07 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 530 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:39:08 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:57:00 +0800] "GET /1 HTTP/1.1" 404 494 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:57:01 +0800] "GET /1 HTTP/1.1" 404 493 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:57:10 +0800] "POST /DVWA/login.php HTTP/1.1" 302 337 "http://192.168.2.61/DVWA/login.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:57:10 +0800] "GET /DVWA/index.php HTTP/1.1" 200 3081 "http://192.168.2.61/DVWA/login.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:57:12 +0800] "GET /DVWA/vulnerabilities/fi/?page=include.php HTTP/1.1" 200 1653 "http://192.168.2.61/DVWA/index.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:57:12 +0800] "GET /DVWA/vulnerabilities/exec/ HTTP/1.1" 200 1751 "http://192.168.2.61/DVWA/vulnerabilities/fi/?page=include.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:57:14 +0800] "GET /DVWA/vulnerabilities/upload/ HTTP/1.1" 200 1784 "http://192.168.2.61/DVWA/vulnerabilities/exec/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:57:15 +0800] "GET /DVWA/vulnerabilities/captcha/ HTTP/1.1" 200 1874 "http://192.168.2.61/DVWA/vulnerabilities/upload/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:57:15 +0800] "GET /DVWA/vulnerabilities/sqli/ HTTP/1.1" 200 1805 "http://192.168.2.61/DVWA/vulnerabilities/captcha/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:57:18 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:57:40 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 530 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:02:15:42 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 530 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:02:15:42 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:28 +0800] "GET / HTTP/1.1" 200 754 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:28 +0800] "GET /icons/unknown.gif HTTP/1.1" 200 528 "http://192.168.2.61/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:28 +0800] "GET /favicon.ico HTTP/1.1" 404 503 "http://192.168.2.61/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:30 +0800] "GET /phpinfo.php HTTP/1.1" 200 24645 "http://192.168.2.61/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:32 +0800] "GET /DVWA/ HTTP/1.1" 302 478 "http://192.168.2.61/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:32 +0800] "GET /DVWA/login.php HTTP/1.1" 200 1049 "http://192.168.2.61/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:32 +0800] "GET /DVWA/dvwa/images/login_logo.png HTTP/1.1" 304 182 "http://192.168.2.61/DVWA/login.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:32 +0800] "GET /DVWA/dvwa/css/login.css HTTP/1.1" 200 741 "http://192.168.2.61/DVWA/login.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:35 +0800] "POST /DVWA/login.php HTTP/1.1" 302 336 "http://192.168.2.61/DVWA/login.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:38 +0800] "GET /DVWA/index.php HTTP/1.1" 200 3081 "http://192.168.2.61/DVWA/login.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:38 +0800] "GET /DVWA/dvwa/css/main.css HTTP/1.1" 200 1445 "http://192.168.2.61/DVWA/index.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:38 +0800] "GET /DVWA/dvwa/js/dvwaPage.js HTTP/1.1" 200 809 "http://192.168.2.61/DVWA/index.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:38 +0800] "GET /DVWA/dvwa/images/logo.png HTTP/1.1" 304 181 "http://192.168.2.61/DVWA/index.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:40 +0800] "GET /DVWA/vulnerabilities/upload/ HTTP/1.1" 200 1784 "http://192.168.2.61/DVWA/index.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:40 +0800] "GET /DVWA/vulnerabilities/fi/?page=include.php HTTP/1.1" 200 1653 "http://192.168.2.61/DVWA/vulnerabilities/upload/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:41 +0800] "GET /DVWA/vulnerabilities/upload/ HTTP/1.1" 200 1784 "http://192.168.2.61/DVWA/vulnerabilities/fi/?page=include.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:41 +0800] "GET /DVWA/vulnerabilities/captcha/ HTTP/1.1" 200 1874 "http://192.168.2.61/DVWA/vulnerabilities/upload/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:42 +0800] "GET /DVWA/vulnerabilities/sqli/ HTTP/1.1" 200 1805 "http://192.168.2.61/DVWA/vulnerabilities/captcha/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:44 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.194 - - [12/Apr/2018:03:51:59 +0800] "GET / HTTP/1.0" 200 1539 "-" "-"
172.20.168.194 - - [12/Apr/2018:03:52:12 +0800] "GET / HTTP/1.0" 200 1539 "-" "-"
120.114.133.79 - - [12/Apr/2018:04:34:07 +0800] "GET /phpinfo.php HTTP/1.1" 200 24617 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/61.0.3163.100 Safari/537.36"
120.114.133.79 - - [12/Apr/2018:04:34:08 +0800] "GET /favicon.ico HTTP/1.1" 404 504 "http://172.20.168.86/phpinfo.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/61.0.3163.100 Safari/537.36"
120.114.135.25 - - [12/Apr/2018:04:34:44 +0800] "GET /phpinfo.php HTTP/1.1" 200 24444 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; ASJB; ASJB; MAAU; rv:11.0) like Gecko"
120.114.135.25 - - [12/Apr/2018:04:34:44 +0800] "GET /favicon.ico HTTP/1.1" 404 505 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64; Trident/7.0; ASJB; MAAU; rv:11.0) like Gecko"
120.114.133.79 - - [12/Apr/2018:04:35:41 +0800] "GET /DVWA HTTP/1.1" 301 576 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/61.0.3163.100 Safari/537.36"
120.114.133.79 - - [12/Apr/2018:04:35:41 +0800] "GET /DVWA/ HTTP/1.1" 302 478 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/61.0.3163.100 Safari/537.36"
120.114.133.79 - - [12/Apr/2018:04:35:41 +0800] "GET /DVWA/login.php HTTP/1.1" 200 1047 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/61.0.3163.100 Safari/537.36"
120.114.133.79 - - [12/Apr/2018:04:35:41 +0800] "GET /DVWA/dvwa/css/login.css HTTP/1.1" 200 741 "http://172.20.168.86/DVWA/login.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/61.0.3163.100 Safari/537.36"
120.114.133.79 - - [12/Apr/2018:04:35:41 +0800] "GET /DVWA/dvwa/images/login_logo.png HTTP/1.1" 200 9375 "http://172.20.168.86/DVWA/login.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/61.0.3163.100 Safari/537.36"


```

### cat error.log

```
[Thu Apr 12 00:09:46.000543 2018] [mpm_prefork:notice] [pid 1119] AH00163: Apach
e/2.4.18 (Ubuntu) configured -- resuming normal operations
[Thu Apr 12 00:09:46.000641 2018] [core:notice] [pid 1119] AH00094: Command line
: '/usr/sbin/apache2'
[Thu Apr 12 00:11:25.876345 2018] [mpm_prefork:notice] [pid 1119] AH00169: caugh
t SIGTERM, shutting down
[Thu Apr 12 00:11:28.000791 2018] [:notice] [pid 1714] ModSecurity for Apache/2.
9.0 (http://www.modsecurity.org/) configured.
[Thu Apr 12 00:11:28.001034 2018] [:notice] [pid 1714] ModSecurity: APR compiled
 version="1.5.1"; loaded version="1.5.2"
[Thu Apr 12 00:11:28.001066 2018] [:warn] [pid 1714] ModSecurity: Loaded APR do
not match with compiled!
[Thu Apr 12 00:11:28.001096 2018] [:notice] [pid 1714] ModSecurity: PCRE compile
d version="8.35 "; loaded version="8.38 2015-11-23"
[Thu Apr 12 00:11:28.001126 2018] [:warn] [pid 1714] ModSecurity: Loaded PCRE do
 not match with compiled!
[Thu Apr 12 00:11:28.001152 2018] [:notice] [pid 1714] ModSecurity: LUA compiled
 version="Lua 5.1"
[Thu Apr 12 00:11:28.001177 2018] [:notice] [pid 1714] ModSecurity: YAJL compile
d version="2.1.0"
[Thu Apr 12 00:11:28.001203 2018] [:notice] [pid 1714] ModSecurity: LIBXML compi
led version="2.9.2"
[Thu Apr 12 00:11:28.001369 2018] [:notice] [pid 1714] ModSecurity: StatusEngine

```

### cat access.log

```

192.168.2.50 - - [12/Apr/2018:00:12:14 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 530 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:12:14 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:12:14 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:22:19 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 530 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:22:19 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:22:19 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:26:39 +0800] "GET /1 HTTP/1.1" 404 494 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:26:40 +0800] "GET /1 HTTP/1.1" 404 493 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:26:42 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:26:42 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:27:37 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 530 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:27:37 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:30:24 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 530 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:30:25 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 530 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:30:25 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:33:12 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 530 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:33:12 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:33:32 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 530 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:33:32 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:33:44 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 530 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:33:45 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:33:47 +0800] "GET /DVWA/vulnerabilities/sqli/ HTTP/1.1" 200 1805 "http://192.168.2.61/DVWA/vulnerabilities/captcha/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:33:47 +0800] "GET /DVWA/favicon.ico HTTP/1.1" 200 1706 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:33:48 +0800] "GET /DVWA/vulnerabilities/sqli/ HTTP/1.1" 200 1805 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:33:50 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:35:08 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 530 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:35:08 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:35:09 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:39:07 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 530 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:39:08 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:57:00 +0800] "GET /1 HTTP/1.1" 404 494 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:57:01 +0800] "GET /1 HTTP/1.1" 404 493 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:57:10 +0800] "POST /DVWA/login.php HTTP/1.1" 302 337 "http://192.168.2.61/DVWA/login.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:57:10 +0800] "GET /DVWA/index.php HTTP/1.1" 200 3081 "http://192.168.2.61/DVWA/login.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:57:12 +0800] "GET /DVWA/vulnerabilities/fi/?page=include.php HTTP/1.1" 200 1653 "http://192.168.2.61/DVWA/index.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:57:12 +0800] "GET /DVWA/vulnerabilities/exec/ HTTP/1.1" 200 1751 "http://192.168.2.61/DVWA/vulnerabilities/fi/?page=include.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:57:14 +0800] "GET /DVWA/vulnerabilities/upload/ HTTP/1.1" 200 1784 "http://192.168.2.61/DVWA/vulnerabilities/exec/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:57:15 +0800] "GET /DVWA/vulnerabilities/captcha/ HTTP/1.1" 200 1874 "http://192.168.2.61/DVWA/vulnerabilities/upload/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:57:15 +0800] "GET /DVWA/vulnerabilities/sqli/ HTTP/1.1" 200 1805 "http://192.168.2.61/DVWA/vulnerabilities/captcha/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:57:18 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:00:57:40 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 530 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:02:15:42 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 530 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:02:15:42 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:28 +0800] "GET / HTTP/1.1" 200 754 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:28 +0800] "GET /icons/unknown.gif HTTP/1.1" 200 528 "http://192.168.2.61/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:28 +0800] "GET /favicon.ico HTTP/1.1" 404 503 "http://192.168.2.61/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:30 +0800] "GET /phpinfo.php HTTP/1.1" 200 24645 "http://192.168.2.61/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:32 +0800] "GET /DVWA/ HTTP/1.1" 302 478 "http://192.168.2.61/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:32 +0800] "GET /DVWA/login.php HTTP/1.1" 200 1049 "http://192.168.2.61/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:32 +0800] "GET /DVWA/dvwa/images/login_logo.png HTTP/1.1" 304 182 "http://192.168.2.61/DVWA/login.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:32 +0800] "GET /DVWA/dvwa/css/login.css HTTP/1.1" 200 741 "http://192.168.2.61/DVWA/login.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:35 +0800] "POST /DVWA/login.php HTTP/1.1" 302 336 "http://192.168.2.61/DVWA/login.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:38 +0800] "GET /DVWA/index.php HTTP/1.1" 200 3081 "http://192.168.2.61/DVWA/login.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:38 +0800] "GET /DVWA/dvwa/css/main.css HTTP/1.1" 200 1445 "http://192.168.2.61/DVWA/index.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:38 +0800] "GET /DVWA/dvwa/js/dvwaPage.js HTTP/1.1" 200 809 "http://192.168.2.61/DVWA/index.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:38 +0800] "GET /DVWA/dvwa/images/logo.png HTTP/1.1" 304 181 "http://192.168.2.61/DVWA/index.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:40 +0800] "GET /DVWA/vulnerabilities/upload/ HTTP/1.1" 200 1784 "http://192.168.2.61/DVWA/index.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:40 +0800] "GET /DVWA/vulnerabilities/fi/?page=include.php HTTP/1.1" 200 1653 "http://192.168.2.61/DVWA/vulnerabilities/upload/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:41 +0800] "GET /DVWA/vulnerabilities/upload/ HTTP/1.1" 200 1784 "http://192.168.2.61/DVWA/vulnerabilities/fi/?page=include.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:41 +0800] "GET /DVWA/vulnerabilities/captcha/ HTTP/1.1" 200 1874 "http://192.168.2.61/DVWA/vulnerabilities/upload/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:42 +0800] "GET /DVWA/vulnerabilities/sqli/ HTTP/1.1" 200 1805 "http://192.168.2.61/DVWA/vulnerabilities/captcha/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
192.168.2.50 - - [12/Apr/2018:03:50:44 +0800] "GET /DVWA/vulnerabilities/sqli/?id=%27+or+1%3D1&Submit=Submit HTTP/1.1" 403 529 "http://192.168.2.61/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.194 - - [12/Apr/2018:03:51:59 +0800] "GET / HTTP/1.0" 200 1539 "-" "-"
172.20.168.194 - - [12/Apr/2018:03:52:12 +0800] "GET / HTTP/1.0" 200 1539 "-" "-"
120.114.133.79 - - [12/Apr/2018:04:34:07 +0800] "GET /phpinfo.php HTTP/1.1" 200 24617 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/61.0.3163.100 Safari/537.36"
120.114.133.79 - - [12/Apr/2018:04:34:08 +0800] "GET /favicon.ico HTTP/1.1" 404 504 "http://172.20.168.86/phpinfo.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/61.0.3163.100 Safari/537.36"
120.114.135.25 - - [12/Apr/2018:04:34:44 +0800] "GET /phpinfo.php HTTP/1.1" 200 24444 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; ASJB; ASJB; MAAU; rv:11.0) like Gecko"
120.114.135.25 - - [12/Apr/2018:04:34:44 +0800] "GET /favicon.ico HTTP/1.1" 404 505 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64; Trident/7.0; ASJB; MAAU; rv:11.0) like Gecko"
120.114.133.79 - - [12/Apr/2018:04:35:41 +0800] "GET /DVWA HTTP/1.1" 301 576 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/61.0.3163.100 Safari/537.36"
120.114.133.79 - - [12/Apr/2018:04:35:41 +0800] "GET /DVWA/ HTTP/1.1" 302 478 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/61.0.3163.100 Safari/537.36"
120.114.133.79 - - [12/Apr/2018:04:35:41 +0800] "GET /DVWA/login.php HTTP/1.1" 200 1047 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/61.0.3163.100 Safari/537.36"
120.114.133.79 - - [12/Apr/2018:04:35:41 +0800] "GET /DVWA/dvwa/css/login.css HTTP/1.1" 200 741 "http://172.20.168.86/DVWA/login.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/61.0.3163.100 Safari/537.36"
120.114.133.79 - - [12/Apr/2018:04:35:41 +0800] "GET /DVWA/dvwa/images/login_logo.png HTTP/1.1" 200 9375 "http://172.20.168.86/DVWA/login.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/61.0.3163.100 Safari/537.36"
120.114.135.25 - - [12/Apr/2018:04:39:09 +0800] "GET /DVWA HTTP/1.1" 301 576 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; ASJB; ASJB; MAAU; rv:11.0) like Gecko"
120.114.135.25 - - [12/Apr/2018:04:39:09 +0800] "GET /DVWA/ HTTP/1.1" 302 478 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; ASJB; ASJB; MAAU; rv:11.0) like Gecko"
120.114.135.25 - - [12/Apr/2018:04:39:09 +0800] "GET /DVWA/login.php HTTP/1.1" 200 1049 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; ASJB; ASJB; MAAU; rv:11.0) like Gecko"
120.114.135.25 - - [12/Apr/2018:04:39:09 +0800] "GET /DVWA/dvwa/css/login.css HTTP/1.1" 200 741 "http://172.20.168.86/DVWA/login.php" "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; ASJB; ASJB; MAAU; rv:11.0) like Gecko"
120.114.135.25 - - [12/Apr/2018:04:39:09 +0800] "GET /DVWA/dvwa/images/login_logo.png HTTP/1.1" 200 9375 "http://172.20.168.86/DVWA/login.php" "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; ASJB; ASJB; MAAU; rv:11.0) like Gecko"
120.114.135.25 - - [12/Apr/2018:04:39:09 +0800] "GET /favicon.ico HTTP/1.1" 404 505 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64; Trident/7.0; ASJB; MAAU; rv:11.0) like Gecko"
120.114.135.25 - - [12/Apr/2018:04:39:14 +0800] "POST /DVWA/login.php HTTP/1.1" 302 336 "http://172.20.168.86/DVWA/login.php" "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; ASJB; ASJB; MAAU; rv:11.0) like Gecko"
120.114.135.25 - - [12/Apr/2018:04:39:14 +0800] "GET /DVWA/index.php HTTP/1.1" 200 3081 "http://172.20.168.86/DVWA/login.php" "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; ASJB; ASJB; MAAU; rv:11.0) like Gecko"
120.114.135.25 - - [12/Apr/2018:04:39:14 +0800] "GET /DVWA/dvwa/images/logo.png HTTP/1.1" 200 5331 "http://172.20.168.86/DVWA/index.php" "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; ASJB; ASJB; MAAU; rv:11.0) like Gecko"
120.114.135.25 - - [12/Apr/2018:04:39:14 +0800] "GET /DVWA/dvwa/css/main.css HTTP/1.1" 200 1445 "http://172.20.168.86/DVWA/index.php" "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; ASJB; ASJB; MAAU; rv:11.0) like Gecko"
120.114.135.25 - - [12/Apr/2018:04:39:14 +0800] "GET /DVWA/dvwa/js/dvwaPage.js HTTP/1.1" 200 809 "http://172.20.168.86/DVWA/index.php" "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; ASJB; ASJB; MAAU; rv:11.0) like Gecko"
120.114.135.25 - - [12/Apr/2018:04:39:14 +0800] "GET /DVWA/favicon.ico HTTP/1.1" 200 1707 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64; Trident/7.0; ASJB; MAAU; rv:11.0) like Gecko"
120.114.135.25 - - [12/Apr/2018:04:39:16 +0800] "GET /DVWA/vulnerabilities/sqli/ HTTP/1.1" 200 1805 "http://172.20.168.86/DVWA/index.php" "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; ASJB; ASJB; MAAU; rv:11.0) like Gecko"
120.114.135.25 - - [12/Apr/2018:04:39:17 +0800] "GET /DVWA/vulnerabilities/sqli/?id=1%27+or+%271%27+%3D%271&Submit=Submit HTTP/1.1" 403 530 "http://172.20.168.86/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; ASJB; ASJB; MAAU; rv:11.0) like Gecko"
120.114.135.25 - - [12/Apr/2018:04:39:43 +0800] "GET /DVWA/vulnerabilities/sqli/?id=1%27+or+%271%27+%3D%271&Submit=Submit HTTP/1.1" 403 531 "http://172.20.168.86/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; ASJB; ASJB; MAAU; rv:11.0) like Gecko"
120.114.135.25 - - [12/Apr/2018:04:39:55 +0800] "GET /DVWA/ HTTP/1.1" 200 3058 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; ASJB; ASJB; MAAU; rv:11.0) like Gecko"
172.20.168.106 - - [12/Apr/2018:04:43:03 +0800] "GET / HTTP/1.1" 200 755 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:43:03 +0800] "GET /icons/folder.gif HTTP/1.1" 200 509 "http://172.20.168.86/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:43:03 +0800] "GET /icons/unknown.gif HTTP/1.1" 200 529 "http://172.20.168.86/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:43:03 +0800] "GET /icons/blank.gif HTTP/1.1" 200 431 "http://172.20.168.86/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:43:04 +0800] "GET /favicon.ico HTTP/1.1" 404 504 "http://172.20.168.86/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:43:23 +0800] "GET /DVWA HTTP/1.1" 301 576 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:43:23 +0800] "GET /DVWA/ HTTP/1.1" 302 478 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:43:23 +0800] "GET /DVWA/login.php HTTP/1.1" 200 1048 "-" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:43:23 +0800] "GET /DVWA/dvwa/css/login.css HTTP/1.1" 200 741 "http://172.20.168.86/DVWA/login.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:43:23 +0800] "GET /DVWA/dvwa/images/login_logo.png HTTP/1.1" 200 9375 "http://172.20.168.86/DVWA/login.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:44:24 +0800] "POST /DVWA/login.php HTTP/1.1" 302 337 "http://172.20.168.86/DVWA/login.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:44:24 +0800] "GET /DVWA/index.php HTTP/1.1" 200 3081 "http://172.20.168.86/DVWA/login.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:44:24 +0800] "GET /DVWA/dvwa/css/main.css HTTP/1.1" 200 1445 "http://172.20.168.86/DVWA/index.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:44:24 +0800] "GET /DVWA/dvwa/js/dvwaPage.js HTTP/1.1" 200 809 "http://172.20.168.86/DVWA/index.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:44:24 +0800] "GET /DVWA/dvwa/images/logo.png HTTP/1.1" 200 5330 "http://172.20.168.86/DVWA/index.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:44:24 +0800] "GET /DVWA/favicon.ico HTTP/1.1" 200 1706 "http://172.20.168.86/DVWA/index.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:47:55 +0800] "GET /DVWA/vulnerabilities/sqli/ HTTP/1.1" 200 1806 "http://172.20.168.86/DVWA/index.php" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:47:55 +0800] "GET /DVWA/dvwa/js/dvwaPage.js HTTP/1.1" 200 809 "http://172.20.168.86/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:47:55 +0800] "GET /DVWA/dvwa/css/main.css HTTP/1.1" 200 1445 "http://172.20.168.86/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:47:55 +0800] "GET /DVWA/dvwa/images/logo.png HTTP/1.1" 304 181 "http://172.20.168.86/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:48:23 +0800] "GET /DVWA/vulnerabilities/sqli/?id=1&Submit=Submit HTTP/1.1" 200 1830 "http://172.20.168.86/DVWA/vulnerabilities/sqli/" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:48:23 +0800] "GET /DVWA/dvwa/js/dvwaPage.js HTTP/1.1" 200 809 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=1&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:48:23 +0800] "GET /DVWA/dvwa/css/main.css HTTP/1.1" 200 1445 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=1&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:48:23 +0800] "GET /DVWA/dvwa/images/logo.png HTTP/1.1" 304 181 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=1&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:48:40 +0800] "GET /DVWA/vulnerabilities/sqli/?id=2&Submit=Submit HTTP/1.1" 200 1839 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=1&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:48:40 +0800] "GET /DVWA/dvwa/js/dvwaPage.js HTTP/1.1" 200 809 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=2&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:48:40 +0800] "GET /DVWA/dvwa/css/main.css HTTP/1.1" 200 1445 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=2&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:48:40 +0800] "GET /DVWA/dvwa/images/logo.png HTTP/1.1" 304 181 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=2&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:49:21 +0800] "GET /DVWA/vulnerabilities/sqli/?id=1&Submit=Submit HTTP/1.1" 200 1830 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=2&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:49:21 +0800] "GET /DVWA/dvwa/js/dvwaPage.js HTTP/1.1" 200 809 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=1&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:49:21 +0800] "GET /DVWA/dvwa/css/main.css HTTP/1.1" 200 1445 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=1&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:49:21 +0800] "GET /DVWA/dvwa/images/logo.png HTTP/1.1" 304 181 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=1&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:49:52 +0800] "GET /DVWA/vulnerabilities/sqli/?id=2&Submit=Submit HTTP/1.1" 200 1839 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=1&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:49:53 +0800] "GET /DVWA/dvwa/js/dvwaPage.js HTTP/1.1" 200 809 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=2&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:49:53 +0800] "GET /DVWA/dvwa/css/main.css HTTP/1.1" 200 1445 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=2&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:49:53 +0800] "GET /DVWA/dvwa/images/logo.png HTTP/1.1" 304 181 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=2&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:50:10 +0800] "GET /DVWA/vulnerabilities/sqli/?id=3&Submit=Submit HTTP/1.1" 200 1836 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=2&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:50:10 +0800] "GET /DVWA/dvwa/css/main.css HTTP/1.1" 200 1445 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=3&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:50:10 +0800] "GET /DVWA/dvwa/js/dvwaPage.js HTTP/1.1" 200 809 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=3&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:50:10 +0800] "GET /DVWA/dvwa/images/logo.png HTTP/1.1" 304 181 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=3&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:51:40 +0800] "GET /DVWA/vulnerabilities/sqli/?id=1%27+or++%271%27%3D%271&Submit=Submit HTTP/1.1" 403 531 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=3&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:51:50 +0800] "GET /DVWA/vulnerabilities/sqli/?id=1%27+or+%271%27%3D%271&Submit=Submit HTTP/1.1" 403 531 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=3&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:51:57 +0800] "GET /DVWA/vulnerabilities/sqli/?id=+1%27or+%271%27%3D%271&Submit=Submit HTTP/1.1" 403 531 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=3&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:52:03 +0800] "GET /DVWA/vulnerabilities/sqli/?id=1%27or+%271%27%3D%271&Submit=Submit HTTP/1.1" 403 531 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=3&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:52:19 +0800] "GET /DVWA/vulnerabilities/sqli/?id=1%27or+%271%27%3D%271&Submit=Submit HTTP/1.1" 403 531 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=3&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:52:39 +0800] "GET /DVWA/vulnerabilities/sqli/?id=1%27+or++%271%27%3D%271+&Submit=Submit HTTP/1.1" 403 531 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=3&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:52:51 +0800] "GET /DVWA/vulnerabilities/sqli/?id=1%27+OR++%271%27%3D%271+&Submit=Submit HTTP/1.1" 403 531 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=3&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:53:01 +0800] "GET /DVWA/vulnerabilities/sqli/?id=1%27+OR++%271%27%3D%271+&Submit=Submit HTTP/1.1" 403 531 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=3&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:53:26 +0800] "GET /DVWA/vulnerabilities/sqli/?id=1%27+or++%271%27%3D%271+&Submit=Submit HTTP/1.1" 403 531 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=3&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:54:00 +0800] "GET /DVWA/vulnerabilities/sqli/?id=1%27+or++%271%27+%3D+1+&Submit=Submit HTTP/1.1" 403 531 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=3&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:54:06 +0800] "GET /DVWA/vulnerabilities/sqli/?id=1%27+or++%271%27+%3D+%271+&Submit=Submit HTTP/1.1" 403 531 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=3&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:54:32 +0800] "GET /DVWA/vulnerabilities/sqli/?id=1%27or+%271%27%3D%271+&Submit=Submit HTTP/1.1" 403 531 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=3&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:54:38 +0800] "GET /DVWA/vulnerabilities/sqli/?id=1%27+or+%271%27%3D%271+&Submit=Submit HTTP/1.1" 403 531 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=3&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:55:09 +0800] "GET /DVWA/vulnerabilities/sqli/?id=1%27+or+%271%27%3D%271&Submit=Submit HTTP/1.1" 403 531 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=3&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:55:55 +0800] "GET /DVWA/vulnerabilities/sqli/?id=1%27or+%271%27%3D%271&Submit=Submit HTTP/1.1" 403 531 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=3&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:57:00 +0800] "GET /DVWA/vulnerabilities/sqli/?id=1%27+or+%271%27+%3D+%271&Submit=Submit HTTP/1.1" 403 531 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=3&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:57:09 +0800] "GET /DVWA/vulnerabilities/sqli/?id=1%27+or+%271%27+%3D+%271&Submit=Submit HTTP/1.1" 403 531 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=3&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"
172.20.168.106 - - [12/Apr/2018:04:57:20 +0800] "GET /DVWA/vulnerabilities/sqli/?id=1%27+or+%271%27+%3D+%271&Submit=Submit HTTP/1.1" 403 531 "http://172.20.168.86/DVWA/vulnerabilities/sqli/?id=3&Submit=Submit" "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"


```
### 安裝modsecurity
```
sudo apt-get update
sudo apt-get install libapache2-modsecurity -y

sudo a2enconf fqdn && sudo systemctl reload apache2
sudo  service apache2 reload
sudo apachectl -M | grep --color security2

sudo mv /etc/modsecurity/modsecurity.conf-recommended /etc/modsecurity/modsecurity.conf
sudo service apache2 reload

sudo sed -i "s/SecRuleEngine DetectionOnly/SecRuleEngine On/" /etc/modsecurity/modsecurity.conf
sudo sed -i "s/SecResponseBodyAccess On/SecResponseBodyAccess Off/" /etc/modsecurity/modsecurity.conf
```
