
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
