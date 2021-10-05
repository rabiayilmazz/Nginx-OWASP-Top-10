# Nginx-OWASP-Top-10

# How to install NGINX?
#### 👉[Video](https://www.youtube.com/watch?v=5eRxOYbaIEI&t=1488s)
#### 👉[Documentation](https://www.linode.com/docs/guides/securing-nginx-with-modsecurity/)

```bash
sudo apt-get install bison build-essential ca-certificates curl dh-autoreconf doxygen flex gawk git iputils-ping libcurl4-gnutls-dev libexpat1-dev libgeoip-dev liblmdb-dev libpcre3-dev libpcre++-dev libssl-dev libtool libxml2 libxml2-dev libyajl-dev locales pkg-config wget zlib1g-dev zlibc libgd-dev
sudo apt install git 
```
 ```
cd /opt
git clone https://github.com/SpiderLabs/ModSecurity
cd ModSecurity/
git submodule init
git submodule update
./build.sh
./configure
make
make install
cd ..
sudo git clone --depth 1 https://github.com/SpiderLabs/ModSecurity-nginx.git
nginx -v
sudo wget http://nginx.org/download/nginx-1.18.0.tar.gz
ls
sudo tar -xvzmf nginx-1.18.0.tar.gz
cd nginx-1.18.0
nginx -V
./configure --with-cc-opt='-g -O2 -fdebug-prefix-map=/build/nginx-KTLRnK/nginx-1.18.0=. -fstack-protector-strong -Wformat -Werror=format-security -fPIC -Wdate-time -D_FORTIFY_SOURCE=2' --with-ld-opt='-Wl,-Bsymbolic-functions -Wl,-z,relro -Wl,-z,now -fPIC' --prefix=/usr/share/nginx --conf-path=/etc/nginx/nginx.conf --http-log-path=/var/log/nginx/access.log --error-log-path=/var/log/nginx/error.log --lock-path=/var/lock/nginx.lock --pid-path=/run/nginx.pid --modules-path=/usr/lib/nginx/modules --http-client-body-temp-path=/var/lib/nginx/body --http-fastcgi-temp-path=/var/lib/nginx/fastcgi --http-proxy-temp-path=/var/lib/nginx/proxy --http-scgi-temp-path=/var/lib/nginx/scgi --http-uwsgi-temp-path=/var/lib/nginx/uwsgi --with-debug --with-compat --with-pcre-jit --with-http_ssl_module --with-http_stub_status_module --with-http_realip_module --with-http_auth_request_module --with-http_v2_module --with-http_dav_module --with-http_slice_module --with-threads --with-http_addition_module --with-http_gunzip_module --with-http_gzip_static_module --with-http_image_filter_module=dynamic --with-http_sub_module --with-http_xslt_module=dynamic --with-stream=dynamic --with-stream_ssl_module --with-mail=dynamic --with-mail_ssl_module
make modules
apt install libxslt
apt install libgd-dev
./configure --with-cc-opt='-g -O2 -fdebug-prefix-map=/build/nginx-KTLRnK/nginx-1.18.0=. -fstack-protector-strong -Wformat -Werror=format-security -fPIC -Wdate-time -D_FORTIFY_SOURCE=2' --with-ld-opt='-Wl,-Bsymbolic-functions -Wl,-z,relro -Wl,-z,now -fPIC' --prefix=/usr/share/nginx --conf-path=/etc/nginx/nginx.conf --http-log-path=/var/log/nginx/access.log --error-log-path=/var/log/nginx/error.log --lock-path=/var/lock/nginx.lock --pid-path=/run/nginx.pid --modules-path=/usr/lib/nginx/modules --http-client-body-temp-path=/var/lib/nginx/body --http-fastcgi-temp-path=/var/lib/nginx/fastcgi --http-proxy-temp-path=/var/lib/nginx/proxy --http-scgi-temp-path=/var/lib/nginx/scgi --http-uwsgi-temp-path=/var/lib/nginx/uwsgi --with-debug --with-compat --with-pcre-jit --with-http_ssl_module --with-http_stub_status_module --with-http_realip_module --with-http_auth_request_module --with-http_v2_module --with-http_dav_module --with-http_slice_module --with-threads --with-http_addition_module --with-http_gunzip_module --with-http_gzip_static_module --with-http_image_filter_module=dynamic --with-http_sub_module --with-http_xslt_module=dynamic --with-stream=dynamic --with-stream_ssl_module --with-mail=dynamic --with-mail_ssl_module --add-dynamic-module=../ModSecurity-nginx
apt install libxml2 libxslt
apt install libxslt-dev
./configure --with-cc-opt='-g -O2 -fdebug-prefix-map=/build/nginx-KTLRnK/nginx-1.18.0=. -fstack-protector-strong -Wformat -Werror=format-security -fPIC -Wdate-time -D_FORTIFY_SOURCE=2' --with-ld-opt='-Wl,-Bsymbolic-functions -Wl,-z,relro -Wl,-z,now -fPIC' --prefix=/usr/share/nginx --conf-path=/etc/nginx/nginx.conf --http-log-path=/var/log/nginx/access.log --error-log-path=/var/log/nginx/error.log --lock-path=/var/lock/nginx.lock --pid-path=/run/nginx.pid --modules-path=/usr/lib/nginx/modules --http-client-body-temp-path=/var/lib/nginx/body --http-fastcgi-temp-path=/var/lib/nginx/fastcgi --http-proxy-temp-path=/var/lib/nginx/proxy --http-scgi-temp-path=/var/lib/nginx/scgi --http-uwsgi-temp-path=/var/lib/nginx/uwsgi --with-debug --with-compat --with-pcre-jit --with-http_ssl_module --with-http_stub_status_module --with-http_realip_module --with-http_auth_request_module --with-http_v2_module --with-http_dav_module --with-http_slice_module --with-threads --with-http_addition_module --with-http_gunzip_module --with-http_gzip_static_module --with-http_image_filter_module=dynamic --with-http_sub_module --with-http_xslt_module=dynamic --with-stream=dynamic --with-stream_ssl_module --with-mail=dynamic --with-mail_ssl_module --add-dynamic-module=../ModSecurity-nginx
make modules
sudo mkdir /etc/nginx/modules
ls
ls objs/
sudo cp objs/ngx_http_modsecurity_module.so /etc/nginx/modules
nano /etc/nginx/nginx.conf 
cd /opt
sudo rm -rf /usr/share/modsecurity-crs
git clone https://github.com/coreruleset/coreruleset /usr/local/modsecurity-crs
ls
mv /usr/local/modsecurity-crs/crs-setup.conf.example /usr/local/modsecurity-crs/crs-setup.conf
mv /usr/local/modsecurity-crs/rules/REQUEST-900-EXCLUSION-RULES-BEFORE-CRS.conf.example /usr/local/modsecurity-crs/rules/REQUEST-900-EXCLUSION-RULES-BEFORE-CRS.conf
mkdir -p /etc/nginx/modsec
cp /opt/ModSecurity/unicode.mapping /etc/nginx/modsec
cp /opt/ModSecurity/modsecurity.conf-recommended /etc/nginx/modsec/modsecurity.conf
ModemManager 
cd ModSecurity
ls
nano /etc/nginx/modsec/modsecurity.conf
nano /etc/nginx/modsec/main.conf
nano /etc/nginx/sites-available/default 
sudo systemctl restart nginx
sudo systemctl status nginx
ifconfig
nano /var/log/modsec_audit.log 
cat  /var/log/modsec_audit.log 
cat  /var/log/nginx/access.log  
```

## Owasp Top 10 Lists
* A01:2021-Broken Access Control 
* ***A02:2021-Cryptographic Failures***
* A03:2021-Injection 
* ***A04:2021-Insecure Design*** 
* A05:2021-Security Misconfiguration 
* A06:2021-Vulnerable and Outdated Components 
* A07:2021-Identification and Authentication Failures was previously Broken Authentication 
* ***A08:2021-Software and Data Integrity Failures*** 
* A09:2021-Security Logging and Monitoring Failures 
* A10:2021-Server-Side Request Forgery SSRF

## Attacks
* Broken Authentication http://192.168.1.11/authentication.php?JSESSIONID=0000d8eyYq3L0z2fgq10m4v-rt4:-1
* Cryptographic Failures 
* SQLI https://192.168.1.44/?id=3 or 'a'='a'
* RFI http://192.168.1.44/vuln_page.php?file=http://192.168.1.44/backdoor_
    * http://192.168.1.44/some-page?page=http://192.168.1.44/other-page.htm/malicius-code.php
* LFI http://192.168.1.44/vuln.php?data=O:8:%22Example1%22:1:{s:10:%22cache_file%22;s:15:%22../../index.php%22;}
    * http://192.168.1.44/script.php?page=../../../../../../../../etc/passwd
    * http://192.168.1.44/get-files?file=../../../../some dir/some file
* Monitoring http://192.168.1.44/var/log/nginx/monitoring.log
* Identification and Authentication Failures was previously Broken Authentication http://192.168.1.44/ftp/coupons_2013.md.bak%2500.md
* Component http://192.168.1.44/rabia.php?xml=%3C!ENTITY%20ac%20SYSTEM%20%22php://filter/read=convert.base64-encode/resource=http://example.com/viewlog.php%22%3E]%3E
* Session Fixation http://192.168.1.44/rabia.php?PHPSESSID=qwrtop95340hhty49gjbc84
* XSS http://192.168.1.44/login.php?xml=%3C!DOCTYPE%20replace%20[%3C!ENTITY%20ent%20SYSTEM%20%22file:///etc/shadow%22%3E%20]%3E
    *  http://192.168.1.44/login.php?xml=%3C!ENTITY%20lol2%20%22&lol1;&lol1;&lol1;&lol1;&lol1;&lol1;&lol1;%22%3E
    *  http://192.168.1.44/login.php?xml=%3C!ENTITY%20ac%20SYSTEM%20%22php://filter/read=convert.base64-encode/resource=http://example.com/viewlog.php%22%3E]%3E
    *  http://192.168.1.44/login.php?xml=%3Csvg%20xmlns=%22http://www.w3.org/2000/svg%22%20xmlns:xlink=%22http://www.w3.org/1999/xlink%22%20width=%22300%22%20version=%221.1%22%20height=%22200%22%3E%20%3Cimage%20xlink:href=%22expect://ls%22%3E%3C/image%3E%20%3C/svg%3E
* Access Control with PHP http://192.168.1.44/login.php?xml=%3C!ENTITY%20ac%20SYSTEM%20%22php://filter/read=convert.base64-encode/resource=http://example.com/viewlog.php%22%3E]%3E


