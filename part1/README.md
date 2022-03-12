# Part 1

> This part introduces containerization with Docker and relevant concepts such as *image* and *volume*.

## Exercises

### Exercise 1.1: Getting started

```bash
$ docker ps -a
CONTAINER ID   IMAGE     COMMAND                  CREATED              STATUS                      PORTS     NAMES
d0570fb38baa   nginx     "/docker-entrypoint.…"   About a minute ago   Exited (0) 10 seconds ago             magical_dijkstra
5b5ea8c85697   nginx     "/docker-entrypoint.…"   About a minute ago   Exited (0) 4 seconds ago              wonderful_swanson
e92a35f84654   nginx     "/docker-entrypoint.…"   2 minutes ago        Up 2 minutes                80/tcp    magical_newton
```

### Exercise 1.2: Cleanup

```bash
$ docker ps -as
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES     SIZE

$ docker images
REPOSITORY    TAG       IMAGE ID       CREATED        SIZE
alpine/git    latest    c6b70534b534   2 months ago   27.4MB
hello-world   latest    feb5d9fea6a5   4 months ago   13.3kB
```

### Exercise 1.3: Secret message

```bash
$ docker run -d --name looper devopsdockeruh/simple-web-service:ubuntu
afb6dc147a4a696d083b326ef1143ec49f05568b1f6cb1b6b9e384fe9c85cea1

$ docker exec -it looper bash
root@afb6dc147a4a:/usr/src/app# ls
server  text.log

root@afb6dc147a4a:/usr/src/app# cat text.log
2022-02-23 09:23:37 +0000 UTC
2022-02-23 09:23:39 +0000 UTC
2022-02-23 09:23:41 +0000 UTC
2022-02-23 09:23:43 +0000 UTC
2022-02-23 09:23:45 +0000 UTC
Secret message is: 'You can find the source code here: https://github.com/docker-hy'
```

### Exercise 1.4: Missing dependencies

```bash
$ docker run -d -it ubuntu sh -c "echo 'Input website:'; read website; echo 'Searching..'; sleep 1; curl http://$website;"
eb3d067c0c9ec3fbe7ba353ab0f1d6def758a0fb79c3ed7441c9b338154f9db8

$ docker exec eb3d sh -c "apt-get update && apt-get -y install curl"
Get:1 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]
Get:2 http://archive.ubuntu.com/ubuntu focal InRelease [265 kB]
Get:3 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 Packages [25.8 kB]
Get:4 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages [1546 kB]
Get:5 http://archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Get:6 http://archive.ubuntu.com/ubuntu focal-backports InRelease [108 kB]
Get:7 http://archive.ubuntu.com/ubuntu focal/universe amd64 Packages [11.3 MB]
Get:8 http://security.ubuntu.com/ubuntu focal-security/restricted amd64 Packages [961 kB]
Get:9 http://security.ubuntu.com/ubuntu focal-security/universe amd64 Packages [840 kB]
Get:10 http://archive.ubuntu.com/ubuntu focal/multiverse amd64 Packages [177 kB]
Get:11 http://archive.ubuntu.com/ubuntu focal/main amd64 Packages [1275 kB]
Get:12 http://archive.ubuntu.com/ubuntu focal/restricted amd64 Packages [33.4 kB]
Get:13 http://archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 Packages [29.4 kB]
Get:14 http://archive.ubuntu.com/ubuntu focal-updates/restricted amd64 Packages [1030 kB]
Get:15 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [1134 kB]
Get:16 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [1973 kB]
Get:17 http://archive.ubuntu.com/ubuntu focal-backports/main amd64 Packages [50.8 kB]
Get:18 http://archive.ubuntu.com/ubuntu focal-backports/universe amd64 Packages [24.8 kB]
Fetched 21.0 MB in 1min 6s (317 kB/s)
Reading package lists...
Reading package lists...
Building dependency tree...
Reading state information...
The following additional packages will be installed:
  ca-certificates krb5-locales libasn1-8-heimdal libbrotli1 libcurl4
  libgssapi-krb5-2 libgssapi3-heimdal libhcrypto4-heimdal libheimbase1-heimdal
  libheimntlm0-heimdal libhx509-5-heimdal libk5crypto3 libkeyutils1
  libkrb5-26-heimdal libkrb5-3 libkrb5support0 libldap-2.4-2 libldap-common
  libnghttp2-14 libpsl5 libroken18-heimdal librtmp1 libsasl2-2
  libsasl2-modules libsasl2-modules-db libsqlite3-0 libssh-4 libssl1.1
  libwind0-heimdal openssl publicsuffix
Suggested packages:
  krb5-doc krb5-user libsasl2-modules-gssapi-mit
  | libsasl2-modules-gssapi-heimdal libsasl2-modules-ldap libsasl2-modules-otp
  libsasl2-modules-sql
The following NEW packages will be installed:
  ca-certificates curl krb5-locales libasn1-8-heimdal libbrotli1 libcurl4
  libgssapi-krb5-2 libgssapi3-heimdal libhcrypto4-heimdal libheimbase1-heimdal
  libheimntlm0-heimdal libhx509-5-heimdal libk5crypto3 libkeyutils1
  libkrb5-26-heimdal libkrb5-3 libkrb5support0 libldap-2.4-2 libldap-common
  libnghttp2-14 libpsl5 libroken18-heimdal librtmp1 libsasl2-2
  libsasl2-modules libsasl2-modules-db libsqlite3-0 libssh-4 libssl1.1
  libwind0-heimdal openssl publicsuffix
0 upgraded, 32 newly installed, 0 to remove and 9 not upgraded.
Need to get 5447 kB of archives.
After this operation, 16.7 MB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 libssl1.1 amd64 1.1.1f-1ubuntu2.10 [1322 kB]
Get:2 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 openssl amd64 1.1.1f-1ubuntu2.10 [620 kB]
Get:3 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 ca-certificates all 20210119~20.04.2 [145 kB]
Get:4 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 libsqlite3-0 amd64 3.31.1-4ubuntu0.2 [549 kB]
Get:5 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 krb5-locales all 1.17-6ubuntu4.1 [11.4 kB]
Get:6 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 libkrb5support0 amd64 1.17-6ubuntu4.1 [30.9 kB]
Get:7 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 libk5crypto3 amd64 1.17-6ubuntu4.1 [79.9 kB]
Get:8 http://archive.ubuntu.com/ubuntu focal/main amd64 libkeyutils1 amd64 1.6-6ubuntu1 [10.2 kB]
Get:9 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 libkrb5-3 amd64 1.17-6ubuntu4.1 [330 kB]
Get:10 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 libgssapi-krb5-2 amd64 1.17-6ubuntu4.1 [121 kB]
Get:11 http://archive.ubuntu.com/ubuntu focal/main amd64 libpsl5 amd64 0.21.0-1ubuntu1 [51.5 kB]
Get:12 http://archive.ubuntu.com/ubuntu focal/main amd64 publicsuffix all 20200303.0012-1 [111 kB]
Get:13 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 libbrotli1 amd64 1.0.7-6ubuntu0.1 [267 kB]
Get:14 http://archive.ubuntu.com/ubuntu focal/main amd64 libroken18-heimdal amd64 7.7.0+dfsg-1ubuntu1 [41.8 kB]
Get:15 http://archive.ubuntu.com/ubuntu focal/main amd64 libasn1-8-heimdal amd64 7.7.0+dfsg-1ubuntu1 [181 kB]
Get:16 http://archive.ubuntu.com/ubuntu focal/main amd64 libheimbase1-heimdal amd64 7.7.0+dfsg-1ubuntu1 [29.7 kB]
Get:17 http://archive.ubuntu.com/ubuntu focal/main amd64 libhcrypto4-heimdal amd64 7.7.0+dfsg-1ubuntu1 [87.9 kB]
Get:18 http://archive.ubuntu.com/ubuntu focal/main amd64 libwind0-heimdal amd64 7.7.0+dfsg-1ubuntu1 [48.0 kB]
Get:19 http://archive.ubuntu.com/ubuntu focal/main amd64 libhx509-5-heimdal amd64 7.7.0+dfsg-1ubuntu1 [107 kB]
Get:20 http://archive.ubuntu.com/ubuntu focal/main amd64 libkrb5-26-heimdal amd64 7.7.0+dfsg-1ubuntu1 [208 kB]
Get:21 http://archive.ubuntu.com/ubuntu focal/main amd64 libheimntlm0-heimdal amd64 7.7.0+dfsg-1ubuntu1 [15.1 kB]
Get:22 http://archive.ubuntu.com/ubuntu focal/main amd64 libgssapi3-heimdal amd64 7.7.0+dfsg-1ubuntu1 [96.1 kB]
Get:23 http://archive.ubuntu.com/ubuntu focal/main amd64 libsasl2-modules-db amd64 2.1.27+dfsg-2 [14.9 kB]
Get:24 http://archive.ubuntu.com/ubuntu focal/main amd64 libsasl2-2 amd64 2.1.27+dfsg-2 [49.3 kB]
Get:25 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 libldap-common all 2.4.49+dfsg-2ubuntu1.8 [16.6 kB]
Get:26 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 libldap-2.4-2 amd64 2.4.49+dfsg-2ubuntu1.8 [155 kB]
Get:27 http://archive.ubuntu.com/ubuntu focal/main amd64 libnghttp2-14 amd64 1.40.0-1build1 [78.7 kB]
Get:28 http://archive.ubuntu.com/ubuntu focal/main amd64 librtmp1 amd64 2.4+20151223.gitfa8646d.1-2build1 [54.9 kB]
Get:29 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 libssh-4 amd64 0.9.3-2ubuntu2.2 [170 kB]
Get:30 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 libcurl4 amd64 7.68.0-1ubuntu2.7 [234 kB]
Get:31 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 curl amd64 7.68.0-1ubuntu2.7 [161 kB]
Get:32 http://archive.ubuntu.com/ubuntu focal/main amd64 libsasl2-modules amd64 2.1.27+dfsg-2 [49.1 kB]
debconf: delaying package configuration, since apt-utils is not installed
Fetched 5447 kB in 28s (194 kB/s)
Selecting previously unselected package libssl1.1:amd64.
(Reading database ... 4127 files and directories currently installed.)
Preparing to unpack .../00-libssl1.1_1.1.1f-1ubuntu2.10_amd64.deb ...
Unpacking libssl1.1:amd64 (1.1.1f-1ubuntu2.10) ...
Selecting previously unselected package openssl.
Preparing to unpack .../01-openssl_1.1.1f-1ubuntu2.10_amd64.deb ...
Unpacking openssl (1.1.1f-1ubuntu2.10) ...
Selecting previously unselected package ca-certificates.
Preparing to unpack .../02-ca-certificates_20210119~20.04.2_all.deb ...
Unpacking ca-certificates (20210119~20.04.2) ...
Selecting previously unselected package libsqlite3-0:amd64.
Preparing to unpack .../03-libsqlite3-0_3.31.1-4ubuntu0.2_amd64.deb ...
Unpacking libsqlite3-0:amd64 (3.31.1-4ubuntu0.2) ...
Selecting previously unselected package krb5-locales.
Preparing to unpack .../04-krb5-locales_1.17-6ubuntu4.1_all.deb ...
Unpacking krb5-locales (1.17-6ubuntu4.1) ...
Selecting previously unselected package libkrb5support0:amd64.
Preparing to unpack .../05-libkrb5support0_1.17-6ubuntu4.1_amd64.deb ...
Unpacking libkrb5support0:amd64 (1.17-6ubuntu4.1) ...
Selecting previously unselected package libk5crypto3:amd64.
Preparing to unpack .../06-libk5crypto3_1.17-6ubuntu4.1_amd64.deb ...
Unpacking libk5crypto3:amd64 (1.17-6ubuntu4.1) ...
Selecting previously unselected package libkeyutils1:amd64.
Preparing to unpack .../07-libkeyutils1_1.6-6ubuntu1_amd64.deb ...
Unpacking libkeyutils1:amd64 (1.6-6ubuntu1) ...
Selecting previously unselected package libkrb5-3:amd64.
Preparing to unpack .../08-libkrb5-3_1.17-6ubuntu4.1_amd64.deb ...
Unpacking libkrb5-3:amd64 (1.17-6ubuntu4.1) ...
Selecting previously unselected package libgssapi-krb5-2:amd64.
Preparing to unpack .../09-libgssapi-krb5-2_1.17-6ubuntu4.1_amd64.deb ...
Unpacking libgssapi-krb5-2:amd64 (1.17-6ubuntu4.1) ...
Selecting previously unselected package libpsl5:amd64.
Preparing to unpack .../10-libpsl5_0.21.0-1ubuntu1_amd64.deb ...
Unpacking libpsl5:amd64 (0.21.0-1ubuntu1) ...
Selecting previously unselected package publicsuffix.
Preparing to unpack .../11-publicsuffix_20200303.0012-1_all.deb ...
Unpacking publicsuffix (20200303.0012-1) ...
Selecting previously unselected package libbrotli1:amd64.
Preparing to unpack .../12-libbrotli1_1.0.7-6ubuntu0.1_amd64.deb ...
Unpacking libbrotli1:amd64 (1.0.7-6ubuntu0.1) ...
Selecting previously unselected package libroken18-heimdal:amd64.
Preparing to unpack .../13-libroken18-heimdal_7.7.0+dfsg-1ubuntu1_amd64.deb ...
Unpacking libroken18-heimdal:amd64 (7.7.0+dfsg-1ubuntu1) ...
Selecting previously unselected package libasn1-8-heimdal:amd64.
Preparing to unpack .../14-libasn1-8-heimdal_7.7.0+dfsg-1ubuntu1_amd64.deb ...
Unpacking libasn1-8-heimdal:amd64 (7.7.0+dfsg-1ubuntu1) ...
Selecting previously unselected package libheimbase1-heimdal:amd64.
Preparing to unpack .../15-libheimbase1-heimdal_7.7.0+dfsg-1ubuntu1_amd64.deb ...
Unpacking libheimbase1-heimdal:amd64 (7.7.0+dfsg-1ubuntu1) ...
Selecting previously unselected package libhcrypto4-heimdal:amd64.
Preparing to unpack .../16-libhcrypto4-heimdal_7.7.0+dfsg-1ubuntu1_amd64.deb ...
Unpacking libhcrypto4-heimdal:amd64 (7.7.0+dfsg-1ubuntu1) ...
Selecting previously unselected package libwind0-heimdal:amd64.
Preparing to unpack .../17-libwind0-heimdal_7.7.0+dfsg-1ubuntu1_amd64.deb ...
Unpacking libwind0-heimdal:amd64 (7.7.0+dfsg-1ubuntu1) ...
Selecting previously unselected package libhx509-5-heimdal:amd64.
Preparing to unpack .../18-libhx509-5-heimdal_7.7.0+dfsg-1ubuntu1_amd64.deb ...
Unpacking libhx509-5-heimdal:amd64 (7.7.0+dfsg-1ubuntu1) ...
Selecting previously unselected package libkrb5-26-heimdal:amd64.
Preparing to unpack .../19-libkrb5-26-heimdal_7.7.0+dfsg-1ubuntu1_amd64.deb ...
Unpacking libkrb5-26-heimdal:amd64 (7.7.0+dfsg-1ubuntu1) ...
Selecting previously unselected package libheimntlm0-heimdal:amd64.
Preparing to unpack .../20-libheimntlm0-heimdal_7.7.0+dfsg-1ubuntu1_amd64.deb ...
Unpacking libheimntlm0-heimdal:amd64 (7.7.0+dfsg-1ubuntu1) ...
Selecting previously unselected package libgssapi3-heimdal:amd64.
Preparing to unpack .../21-libgssapi3-heimdal_7.7.0+dfsg-1ubuntu1_amd64.deb ...
Unpacking libgssapi3-heimdal:amd64 (7.7.0+dfsg-1ubuntu1) ...
Selecting previously unselected package libsasl2-modules-db:amd64.
Preparing to unpack .../22-libsasl2-modules-db_2.1.27+dfsg-2_amd64.deb ...
Unpacking libsasl2-modules-db:amd64 (2.1.27+dfsg-2) ...
Selecting previously unselected package libsasl2-2:amd64.
Preparing to unpack .../23-libsasl2-2_2.1.27+dfsg-2_amd64.deb ...
Unpacking libsasl2-2:amd64 (2.1.27+dfsg-2) ...
Selecting previously unselected package libldap-common.
Preparing to unpack .../24-libldap-common_2.4.49+dfsg-2ubuntu1.8_all.deb ...
Unpacking libldap-common (2.4.49+dfsg-2ubuntu1.8) ...
Selecting previously unselected package libldap-2.4-2:amd64.
Preparing to unpack .../25-libldap-2.4-2_2.4.49+dfsg-2ubuntu1.8_amd64.deb ...
Unpacking libldap-2.4-2:amd64 (2.4.49+dfsg-2ubuntu1.8) ...
Selecting previously unselected package libnghttp2-14:amd64.
Preparing to unpack .../26-libnghttp2-14_1.40.0-1build1_amd64.deb ...
Unpacking libnghttp2-14:amd64 (1.40.0-1build1) ...
Selecting previously unselected package librtmp1:amd64.
Preparing to unpack .../27-librtmp1_2.4+20151223.gitfa8646d.1-2build1_amd64.deb ...
Unpacking librtmp1:amd64 (2.4+20151223.gitfa8646d.1-2build1) ...
Selecting previously unselected package libssh-4:amd64.
Preparing to unpack .../28-libssh-4_0.9.3-2ubuntu2.2_amd64.deb ...
Unpacking libssh-4:amd64 (0.9.3-2ubuntu2.2) ...
Selecting previously unselected package libcurl4:amd64.
Preparing to unpack .../29-libcurl4_7.68.0-1ubuntu2.7_amd64.deb ...
Unpacking libcurl4:amd64 (7.68.0-1ubuntu2.7) ...
Selecting previously unselected package curl.
Preparing to unpack .../30-curl_7.68.0-1ubuntu2.7_amd64.deb ...
Unpacking curl (7.68.0-1ubuntu2.7) ...
Selecting previously unselected package libsasl2-modules:amd64.
Preparing to unpack .../31-libsasl2-modules_2.1.27+dfsg-2_amd64.deb ...
Unpacking libsasl2-modules:amd64 (2.1.27+dfsg-2) ...
Setting up libkeyutils1:amd64 (1.6-6ubuntu1) ...
Setting up libpsl5:amd64 (0.21.0-1ubuntu1) ...
Setting up libssl1.1:amd64 (1.1.1f-1ubuntu2.10) ...
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (Can't locate Term/ReadLine.pm in @INC (you may need to install the Term::ReadLine module) (@INC contains: /etc/perl /usr/local/lib/x86_64-linux-gnu/perl/5.30.0 /usr/local/share/perl/5.30.0 /usr/lib/x86_64-linux-gnu/perl5/5.30 /usr/share/perl5 /usr/lib/x86_64-linux-gnu/perl/5.30 /usr/share/perl/5.30 /usr/local/lib/site_perl /usr/lib/x86_64-linux-gnu/perl-base) at /usr/share/perl5/Debconf/FrontEnd/Readline.pm line 7.)
debconf: falling back to frontend: Teletype
Setting up libbrotli1:amd64 (1.0.7-6ubuntu0.1) ...
Setting up libsqlite3-0:amd64 (3.31.1-4ubuntu0.2) ...
Setting up libsasl2-modules:amd64 (2.1.27+dfsg-2) ...
Setting up libnghttp2-14:amd64 (1.40.0-1build1) ...
Setting up krb5-locales (1.17-6ubuntu4.1) ...
Setting up libldap-common (2.4.49+dfsg-2ubuntu1.8) ...
Setting up libkrb5support0:amd64 (1.17-6ubuntu4.1) ...
Setting up libsasl2-modules-db:amd64 (2.1.27+dfsg-2) ...
Setting up librtmp1:amd64 (2.4+20151223.gitfa8646d.1-2build1) ...
Setting up libk5crypto3:amd64 (1.17-6ubuntu4.1) ...
Setting up libsasl2-2:amd64 (2.1.27+dfsg-2) ...
Setting up libroken18-heimdal:amd64 (7.7.0+dfsg-1ubuntu1) ...
Setting up libkrb5-3:amd64 (1.17-6ubuntu4.1) ...
Setting up openssl (1.1.1f-1ubuntu2.10) ...
Setting up publicsuffix (20200303.0012-1) ...
Setting up libheimbase1-heimdal:amd64 (7.7.0+dfsg-1ubuntu1) ...
Setting up libasn1-8-heimdal:amd64 (7.7.0+dfsg-1ubuntu1) ...
Setting up libhcrypto4-heimdal:amd64 (7.7.0+dfsg-1ubuntu1) ...
Setting up ca-certificates (20210119~20.04.2) ...
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (Can't locate Term/ReadLine.pm in @INC (you may need to install the Term::ReadLine module) (@INC contains: /etc/perl /usr/local/lib/x86_64-linux-gnu/perl/5.30.0 /usr/local/share/perl/5.30.0 /usr/lib/x86_64-linux-gnu/perl5/5.30 /usr/share/perl5 /usr/lib/x86_64-linux-gnu/perl/5.30 /usr/share/perl/5.30 /usr/local/lib/site_perl /usr/lib/x86_64-linux-gnu/perl-base) at /usr/share/perl5/Debconf/FrontEnd/Readline.pm line 7.)
debconf: falling back to frontend: Teletype
Updating certificates in /etc/ssl/certs...
128 added, 0 removed; done.
Setting up libwind0-heimdal:amd64 (7.7.0+dfsg-1ubuntu1) ...
Setting up libgssapi-krb5-2:amd64 (1.17-6ubuntu4.1) ...
Setting up libssh-4:amd64 (0.9.3-2ubuntu2.2) ...
Setting up libhx509-5-heimdal:amd64 (7.7.0+dfsg-1ubuntu1) ...
Setting up libkrb5-26-heimdal:amd64 (7.7.0+dfsg-1ubuntu1) ...
Setting up libheimntlm0-heimdal:amd64 (7.7.0+dfsg-1ubuntu1) ...
Setting up libgssapi3-heimdal:amd64 (7.7.0+dfsg-1ubuntu1) ...
Setting up libldap-2.4-2:amd64 (2.4.49+dfsg-2ubuntu1.8) ...
Setting up libcurl4:amd64 (7.68.0-1ubuntu2.7) ...
Setting up curl (7.68.0-1ubuntu2.7) ...
Processing triggers for libc-bin (2.31-0ubuntu9.2) ...
Processing triggers for ca-certificates (20210119~20.04.2) ...
Updating certificates in /etc/ssl/certs...
0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d...
done.

$ docker attach eb3d
helsinki.fi
Searching..
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="https://www.helsinki.fi/">here</a>.</p>
</body></html>
```

### Exercise 1.5: Sizes of images

```bash
$ docker image ls
REPOSITORY                          TAG       IMAGE ID       CREATED         SIZE
devopsdockeruh/simple-web-service   ubuntu    4e3362e907d5   11 months ago   83MB
devopsdockeruh/simple-web-service   alpine    fd312adc88e0   11 months ago   15.7MB

$ docker run -d --name looper devopsdockeruh/simple-web-service:alpine
cd955eafe7a3e252f9d38703c515513d4c874c708dc3b46559313103cca66b8f

$ docker exec -it looper sh
/usr/src/app # ls
server  text.log

/usr/src/app # cat text.log
2022-02-23 09:18:22 +0000 UTC
2022-02-23 09:18:24 +0000 UTC
2022-02-23 09:18:26 +0000 UTC
2022-02-23 09:18:28 +0000 UTC
2022-02-23 09:18:30 +0000 UTC
Secret message is: 'You can find the source code here: https://github.com/docker-hy'
```

### Exercise 1.6: Hello Docker Hub

```bash
$ docker run -it devopsdockeruh/pull_exercise
Unable to find image 'devopsdockeruh/pull_exercise:latest' locally
latest: Pulling from devopsdockeruh/pull_exercise
8e402f1a9c57: Pull complete
5e2195587d10: Pull complete
6f595b2fc66d: Pull complete
165f32bf4e94: Pull complete
67c4f504c224: Pull complete
Digest: sha256:7c0635934049afb9ca0481fb6a58b16100f990a0d62c8665b9cfb5c9ada8a99f
Status: Downloaded newer image for devopsdockeruh/pull_exercise:latest

Give me the password: basics
You found the correct password. Secret message is:
"This is the secret message"
```

### Exercise 1.7: Two line Dockerfile

```bash
$ docker build ./1.7 -t web-server
[+] Building 0.4s (5/5) FINISHED
 => [internal] load build definition from Dockerfile                                          0.0s
 => => transferring dockerfile: 96B                                                           0.0s
 => [internal] load .dockerignore                                                             0.0s
 => => transferring context: 2B                                                               0.0s
 => [internal] load metadata for docker.io/devopsdockeruh/simple-web-service:alpine           0.0s
 => [1/1] FROM docker.io/devopsdockeruh/simple-web-service:alpine                             0.2s
 => exporting to image                                                                        0.0s
 => => exporting layers                                                                       0.0s
 => => writing image sha256:978fbf315695ef5a3ec2e77ee411c4dcd9aa9b867fbc7ea3d26962545fda0585  0.0s
 => => naming to docker.io/library/web-server                                                 0.0s

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them

$ docker run web-server
[GIN-debug] [WARNING] Creating an Engine instance with the Logger and Recovery middleware already attached.

[GIN-debug] [WARNING] Running in "debug" mode. Switch to "release" mode in production.
 - using env:   export GIN_MODE=release
 - using code:  gin.SetMode(gin.ReleaseMode)

[GIN-debug] GET    /*path                    --> server.Start.func1 (3 handlers)
[GIN-debug] Listening and serving HTTP on :8080
```

### Exercise 1.8: Image for script

```bash
$ docker build ./1.8 -t curler
[+] Building 2.3s (9/9) FINISHED
 => [internal] load build definition from Dockerfile                                                                     0.0s
 => => transferring dockerfile: 32B                                                                                      0.0s
 => [internal] load .dockerignore                                                                                        0.0s
 => => transferring context: 2B                                                                                          0.0s
 => [internal] load metadata for docker.io/library/ubuntu:20.04                                                          2.0s
 => [1/4] FROM docker.io/library/ubuntu:20.04@sha256:669e010b58baf5beb2836b253c1fd5768333f0d1dbcb834f7c07a4dc93f474be    0.0s
 => [internal] load build context                                                                                        0.0s
 => => transferring context: 30B                                                                                         0.0s
 => CACHED [2/4] WORKDIR /usr/src/app                                                                                    0.0s
 => CACHED [3/4] COPY curler.sh .                                                                                        0.0s
 => CACHED [4/4] RUN apt-get update && apt-get -y install curl                                                           0.0s
 => exporting to image                                                                                                   0.0s
 => => exporting layers                                                                                                  0.0s
 => => writing image sha256:6f70ef2bc4b0835ca8eacc7f31587620896023ce756b10503b60d582b2d816f2                             0.0s
 => => naming to docker.io/library/curler                                                                                0.0s

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them

$ docker run -it curler
Input website:
helsinki.fi
Searching..
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="https://www.helsinki.fi/">here</a>.</p>
</body></html>
: not found: 1:
```

### Exercise 1.9: Volumes

```bash
$ docker run -v ${pwd}/1.9/text.log:/usr/src/app/text.log -d -it devopsdockeruh/simple-web-service
aa250a24f3b7e5dd0e7df545e9e4ef6d50f9ca6079b80f089f3f7d594288ea30
```

### Exercise 1.10: Ports open

```bash
$ docker run -p 127.0.0.1:8080:8080 web-server
[GIN-debug] [WARNING] Creating an Engine instance with the Logger and Recovery middleware already attached.

[GIN-debug] [WARNING] Running in "debug" mode. Switch to "release" mode in production.
 - using env:   export GIN_MODE=release
 - using code:  gin.SetMode(gin.ReleaseMode)

[GIN-debug] GET    /*path                    --> server.Start.func1 (3 handlers)
[GIN-debug] Listening and serving HTTP on :8080
[GIN] 2022/02/25 - 02:55:19 | 200 |        63.3µs |      172.17.0.1 | GET      "/"
[GIN] 2022/02/25 - 02:55:20 | 200 |        29.8µs |      172.17.0.1 | GET      "/favicon.ico"
```

### Exercise 1.11: Spring

The source codes under [1.11](1.11) folder are copied from [spring-example-project](https://github.com/docker-hy/material-applications/tree/main/spring-example-project) except Dockerfile.

```bash
$ docker build ./1.11 -t spring
[+] Building 2233.9s (12/12) FINISHED
 => [internal] load build definition from Dockerfile                                             0.0s 
 => => transferring dockerfile: 32B                                                              0.0s 
 => [internal] load .dockerignore                                                                0.0s 
 => => transferring context: 2B                                                                  0.0s 
 => [internal] load metadata for docker.io/library/openjdk:8                                     2.0s 
 => CACHED [2/7] WORKDIR /usr/src/app                                                            0.0s 
 => CACHED [3/7] COPY spring-example-project .                                                   0.0s 
 => CACHED [4/7] RUN apt-get update                                                              0.0s 
 => CACHED [5/7] RUN apt-get install -y dos2unix                                                 0.0s 
 => CACHED [6/7] RUN find . -type f -print0 | xargs -0 dos2unix                                  0.0s 
 => [7/7] RUN ./mvnw package                                                                  2230.7s 
 => exporting to image                                                                           0.9s 
 => => exporting layers                                                                          0.8s 
 => => writing image sha256:20b789e21f68090c4e5a2be00d9a3b593464ef1f388644a7fb4b920f928d68f2     0.0s 
 => => naming to docker.io/library/spring                                                        0.0s 

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them

$ docker run -p 127.0.0.1:8080:8080 spring
  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::        (v2.1.3.RELEASE)

2022-02-27 02:49:50.916  INFO 7 --- [           main] c.d.dockerexample.DemoApplication        : Starting DemoApplication v1.1.3 on 065222c44ad7 with PID 7 (/usr/src/app/target/docker-example-1.1.3.jar started by root in /usr/src/app)
2022-02-27 02:49:50.921  INFO 7 --- [           main] c.d.dockerexample.DemoApplication        : No active profile set, falling back to default profiles: default
2022-02-27 02:49:53.640  INFO 7 --- [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat initialized with port(s): 8080 (http)
2022-02-27 02:49:53.717  INFO 7 --- [           main] o.apache.catalina.core.StandardService   : Starting service [Tomcat]
2022-02-27 02:49:53.718  INFO 7 --- [           main] org.apache.catalina.core.StandardEngine  : Starting Servlet engine: [Apache Tomcat/9.0.16]
2022-02-27 02:49:53.755  INFO 7 --- [           main] o.a.catalina.core.AprLifecycleListener   : The APR based Apache Tomcat Native library which allows optimal performance in production environments was not found on the java.library.path: [/usr/java/packages/lib/amd64:/usr/lib64:/lib64:/lib:/usr/lib]
2022-02-27 02:49:53.941  INFO 7 --- [           main] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring embedded WebApplicationContext
2022-02-27 02:49:53.942  INFO 7 --- [           main] o.s.web.context.ContextLoader            : Root WebApplicationContext: initialization completed in 2904 ms
2022-02-27 02:49:54.695  INFO 7 --- [           main] o.s.s.concurrent.ThreadPoolTaskExecutor  : Initializing ExecutorService 'applicationTaskExecutor'
2022-02-27 02:49:55.085  INFO 7 --- [           main] o.s.b.a.w.s.WelcomePageHandlerMapping    : Adding welcome page template: index
2022-02-27 02:49:55.442  INFO 7 --- [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat started on port(s): 8080 (http) with context path ''
2022-02-27 02:49:55.451  INFO 7 --- [           main] c.d.dockerexample.DemoApplication        : Started DemoApplication in 5.382 seconds (JVM running for 6.133)
2022-02-27 02:50:12.080  INFO 7 --- [nio-8080-exec-1] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring DispatcherServlet 'dispatcherServlet'
2022-02-27 02:50:12.080  INFO 7 --- [nio-8080-exec-1] o.s.web.servlet.DispatcherServlet        : Initializing Servlet 'dispatcherServlet'
2022-02-27 02:50:12.092  INFO 7 --- [nio-8080-exec-1] o.s.web.servlet.DispatcherServlet        : Completed initialization in 12 ms
```

### Exercise 1.12: Hello, frontend!

The source codes under [1.12](1.12) folder are copied from [example-frontend](https://github.com/docker-hy/material-applications/tree/main/example-frontend) except Dockerfile.

```bash
$ docker build ./1.12 -t frontend
[+] Building 320.6s (12/12) FINISHED
 => [internal] load build definition from Dockerfile                                                                                                      0.1s
 => => transferring context: 34B                                                                                                                          0.0s
 => [internal] load metadata for docker.io/library/node:16                                                                                                2.1s
 => [1/6] FROM docker.io/library/node:16@sha256:61b6cc81ecc3f94f614dca6bfdc5262d15a6618f7aabfbfc6f9f05c935ee753c                                          0.0s
 => [internal] load build context                                                                                                                         0.1s
 => => transferring context: 725.30kB                                                                                                                     0.0s
 => CACHED [2/6] WORKDIR /usr/src/app                                                                                                                     0.0s
 => [3/6] COPY . .                                                                                                                                        0.1s
 => [4/6] RUN npm install                                                                                                                               205.7s
 => [5/6] RUN npm run build                                                                                                                              32.9s
 => [6/6] RUN npm install -g serve                                                                                                                       13.6s
 => exporting to image                                                                                                                                   33.1s
 => => exporting layers                                                                                                                                  33.0s
 => => writing image sha256:f0b305c0310b057ee5244faccfe4fdd4445a5dbc2c2e68fa93ddd891e36c3f32                                                              0.0s
 => => naming to docker.io/library/frontend                                                                                                               0.0s

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them

$ docker run -p 127.0.0.1:5000:5000 frontend
INFO: Accepting connections at http://localhost:5000
```

### Exercise 1.13: Hello, backend!

The source codes under [1.13](1.13) folder are copied from [example-backend](https://github.com/docker-hy/material-applications/tree/main/example-backend) except Dockerfile.

```bash
$ docker build ./1.13 -t backend
[+] Building 0.3s (11/11) FINISHED
 => [internal] load build definition from Dockerfile                                                                                                0.0s 
 => => transferring dockerfile: 217B                                                                                                                0.0s 
 => [internal] load .dockerignore                                                                                                                   0.0s 
 => => transferring context: 34B                                                                                                                    0.0s 
 => [internal] load metadata for docker.io/library/golang:1.16                                                                                      0.0s 
 => [1/6] FROM docker.io/library/golang:1.16                                                                                                        0.0s 
 => [internal] load build context                                                                                                                   0.0s 
 => => transferring context: 499B                                                                                                                   0.0s 
 => CACHED [2/6] WORKDIR /usr/src/app                                                                                                               0.0s 
 => CACHED [3/6] COPY . .                                                                                                                           0.0s 
 => CACHED [4/6] RUN go env -w GOPROXY=https://goproxy.cn                                                                                           0.0s 
 => CACHED [5/6] RUN go build                                                                                                                       0.0s 
 => CACHED [6/6] RUN go test                                                                                                                        0.0s 
 => exporting to image                                                                                                                              0.1s 
 => => exporting layers                                                                                                                             0.0s 
 => => writing image sha256:89d7f959be856bbdf075a745d8156e880a14b19879eda11e40ff9fab39a1cd87                                                        0.0s 
 => => naming to docker.io/library/backend                                                                                                          0.0s 

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them

$ docker run -p 127.0.0.1:8080:8080 backend
[Ex 2.4+] REDIS_HOST env was not passed so redis connection is not initialized
[Ex 2.6+] POSTGRES_HOST env was not passed so postgres connection is not initialized
[GIN-debug] [WARNING] Creating an Engine instance with the Logger and Recovery middleware already attached.

[GIN-debug] [WARNING] Running in "debug" mode. Switch to "release" mode in production.
 - using env:   export GIN_MODE=release
 - using code:  gin.SetMode(gin.ReleaseMode)

[GIN-debug] GET    /ping                     --> server/router.pingpong (4 handlers)
[GIN-debug] GET    /messages                 --> server/controller.GetMessages (4 handlers)
[GIN-debug] POST   /messages                 --> server/controller.CreateMessage (4 handlers)
[GIN-debug] Listening and serving HTTP on :8080
[GIN] 2022/02/28 - 01:26:54 | 404 |          93µs |      172.17.0.1 | GET      "/"
[GIN] 2022/02/28 - 01:26:56 | 404 |        11.9µs |      172.17.0.1 | GET      "/favicon.ico"
[GIN] 2022/02/28 - 01:27:01 | 200 |        18.6µs |      172.17.0.1 | GET      "/ping"
```

### Exercise 1.14: Environment

```bash
$ docker build ./1.12 -t frontend
[+] Building 536.8s (15/15) FINISHED
 => [internal] load build definition from Dockerfile                                                                                                0.0s 
 => => transferring dockerfile: 396B                                                                                                                0.0s 
 => [internal] load .dockerignore                                                                                                                   0.0s 
 => => transferring context: 34B                                                                                                                    0.0s 
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                                                    0.0s 
 => [ 1/10] FROM docker.io/library/ubuntu:latest                                                                                                    0.0s 
 => [internal] load build context                                                                                                                   0.0s 
 => => transferring context: 1.55kB                                                                                                                 0.0s 
 => CACHED [ 2/10] WORKDIR /usr/src/app                                                                                                             0.0s 
 => [ 4/10] RUN apt-get update                                                                                                                     73.4s 
 => [ 5/10] RUN apt-get install -y curl                                                                                                            32.4s
 => [ 6/10] RUN curl -sL https://deb.nodesource.com/setup_16.x | bash                                                                              55.9s
 => [ 7/10] RUN apt install -y nodejs                                                                                                              14.9s
 => [ 8/10] RUN npm install                                                                                                                       313.2s
 => [ 9/10] RUN npm run build                                                                                                                      28.6s
 => [10/10] RUN npm install -g serve                                                                                                                7.0s
 => exporting to image                                                                                                                             10.7s
 => => exporting layers                                                                                                                            10.7s
 => => writing image sha256:24aba9dd2c0eec05cea9ed7e87abfb2d1f38790def5262c0fe69ebe4054f598f                                                        0.0s
 => => naming to docker.io/library/frontend                                                                                                         0.0s

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them

$ docker build ./1.13 -t backend
[+] Building 36.4s (11/11) FINISHED
 => [internal] load build definition from Dockerfile                                                                                                0.1s 
 => => transferring dockerfile: 261B                                                                                                                0.0s 
 => [internal] load .dockerignore                                                                                                                   0.0s 
 => => transferring context: 34B                                                                                                                    0.0s 
 => [internal] load metadata for docker.io/library/golang:1.16                                                                                      0.0s 
 => [internal] load build context                                                                                                                   0.0s 
 => => transferring context: 499B                                                                                                                   0.0s 
 => CACHED [2/6] WORKDIR /usr/src/app                                                                                                               0.0s 
 => CACHED [3/6] COPY . .                                                                                                                           0.0s 
 => [4/6] RUN go env -w GOPROXY=https://goproxy.cn                                                                                                  0.6s 
 => [5/6] RUN go build                                                                                                                             22.2s 
 => [6/6] RUN go test                                                                                                                              11.0s 
 => exporting to image                                                                                                                              2.1s 
 => => exporting layers                                                                                                                             2.1s 
 => => writing image sha256:e62ef56b7b6b0fa820fa414476f5f35dd431925baf41300030630a1c58492c5c                                                        0.0s 
 => => naming to docker.io/library/backend                                                                                                          0.0s 

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them

$ docker run -d -p 127.0.0.1:5000:5000 --name frontend frontend
d3d276e71a9523e20458e87421ab86f9cdc138a79199cfd56f44afe1a8050017

$ docker run -d -p 127.0.0.1:8080:8080 --name backend backend
e6bdc7c5b25d204b7023524ca41930d17c9d61958509f2d1cc5d1929cbdbc7e3
```

### Exercise 1.15: Homework

Please see [zeroto521/curler](https://hub.docker.com/r/zeroto521/curler).

### Exercise 1.16: Heroku

Please see devops-with-docker-exercise.herokuapp.com

```bash
$ docker pull registry.heroku.com
Using default tag: latest
latest: Pulling from devopsdockeruh/coursepage
59bf1c3509f3: Already exists
66fcb0eb5bed: Pull complete
564b5778c99c: Pull complete
596dbe9943ae: Pull complete
cea1aa9397b1: Pull complete
60d3dcca6f10: Pull complete
Digest: sha256:8e8b3117fe9c50b5d8abacb9fac265d6c762d319a4fa61db96b85d7310fc3512
Status: Downloaded newer image for devopsdockeruh/coursepage:latest
docker.io/devopsdockeruh/coursepage:latest

$ docker tag devopsdockeruh/coursepage registry.heroku.com/devops-with-docker-exercise/web

$ docker push registry.heroku.com/devops-with-docker-exercise/web
Using default tag: latest
The push refers to repository [registry.heroku.com/devops-with-docker-exercise/web]
6f413faad0c5: Layer already exists
e15245eff772: Layer already exists
25c4d12b64e7: Layer already exists
1d454e07796f: Layer already exists
970073eeaee3: Pushed
8d3ac3489996: Layer already exists
latest: digest: sha256:8e8b3117fe9c50b5d8abacb9fac265d6c762d319a4fa61db96b85d7310fc3512 size: 1580

$ heroku login
heroku: Press any key to open up the browser to login or q to exit:
Opening browser to https://cli-auth.heroku.com/auth/cli/browser/xxx...xxx
Logging in... done
Logged in as address@domain.com

$ heroku container:login
Login Succeeded

$ heroku container:release web --app devops-with-docker-exercise
Releasing images web to devops-with-docker-exercise... done
```
