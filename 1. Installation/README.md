
### Mac OSX

#### 1. Update Homebrew’s package database.
>$ brew update

#### 2. Install MongoDB

##### Install the MongoDB Binaries
 >$ brew install mongodb

##### Install the MongoDB Binaries with TLS/SSL Support
 >$ brew install mongodb --with-openssl

##### Install the Latest Development Release of MongoDB
 >$ brew install mongodb --devel
 
- Sau khi cài đặt 
 - The databases are stored in the /usr/local/var/mongodb/ directory
 - The mongod.conf file is here: /usr/local/etc/mongod.conf
 - The mongo logs can be found at /usr/local/var/log/mongodb/
 - The mongo binaries are here: /usr/local/Cellar/mongodb/[version]/bin


Start MongoDB
>$ brew services start mongodb

>$ mongo

Shutdown
>$ brew services stop mongodb

For more options
>$ brew info mongodb



## CentOS

#### 1. Tạo file cài đặt 
>$ sudo touch /etc/yum.repos.d/mongodb-org-3.4.repo

Thêm nội dung sau để cài đặt mongo 3.4:
```
[mongodb-org-3.4]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/$releasever/mongodb-org/3.4/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://www.mongodb.org/static/pgp/server-3.4.asc
```

>$ sudo vim /etc/yum.repos.d/mongodb-org-3.4.repo
 - Nhấn A để insert 
 - Paste nội dung trên.
 - Esc -> :wq để lưu nội dung


#### 2. Cài đặt
>$ sudo yum install -y mongodb-org


Start
>$ systemctl start mongod

Check mongo service status
>$ systemctl status mongod


## Window

#### 1. Tải về mongodb
https://www.mongodb.com/download-center#community

#### 2. Cài đặt

Tạo 1 folder mongodata
>$ mkdir C:\Users\mryit\Desktop\mongodata

Start mongo server và data được lưu ở folder ```mongodata```
>$ cd C:\Program Files\MongoDB\Server\3.4\bin\

>$ mongod.exe --dbpath C:\Users\mryit\Desktop\mongodata

Tiếp tục tại folder ```bin```
>$ mongo




