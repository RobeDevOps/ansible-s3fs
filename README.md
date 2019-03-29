## s3fuse installation with ansible

Requirements
----------

Must of the AWS AMI has installed python but for *ubuntu/images/hvm-ssd/ubuntu-bionic-18.04-amd64-server-20190212.1 (ami-0a313d6098716f372)* it required to install python first.

Amazon users based on OS
--------------
Below is the of Amazon OS and associated ssh username

| OS                 | AMI ssh username |
|--------------------|------------------|
|Amazon Linux        | ec2-user         |	
|Ubuntu 	         | ubuntu 	        |
|Debian 	         | admin            |
|RHEL 6.4 and later  | ec2-user         | 	
|RHEL 6.3 and earlier| root             |	
|Fedora              | fedora           |
|Centos              | centos           |
|SUSE                |ec2-user          |


S3fs project structure
-----------------------
Once the s3 fuse is cloned the directory structure should be like this.
```
├── AUTHORS
├── COPYING
├── ChangeLog
├── INSTALL
├── Makefile.am
├── README.md
├── autogen.sh
├── configure.ac
├── doc
│   ├── Makefile.am
│   ├── man
│   │   └── s3fs.1
│   └── s3fs.png
├── src
│   ├── Makefile.am
│   ├── addhead.cpp
│   ├── addhead.h
│   ├── cache.cpp
│   ├── cache.h
│   ├── common.h
│   ├── common_auth.cpp
│   ├── curl.cpp
│   ├── curl.h
│   ├── fdcache.cpp
│   ├── fdcache.h
│   ├── gnutls_auth.cpp
│   ├── nss_auth.cpp
│   ├── openssl_auth.cpp
│   ├── psemaphore.h
│   ├── s3fs.cpp
│   ├── s3fs.h
│   ├── s3fs_auth.h
│   ├── s3fs_util.cpp
│   ├── s3fs_util.h
│   ├── string_util.cpp
│   ├── string_util.h
│   ├── test_string_util.cpp
│   └── test_util.h
└── test
    ├── Makefile.am
    ├── integration-test-common.sh
    ├── integration-test-main.sh
    ├── keystore.jks
    ├── mergedir.sh
    ├── passwd-s3fs
    ├── require-root.sh
    ├── s3proxy.conf
    ├── sample_ahbe.conf
    ├── sample_delcache.sh
    ├── small-integration-test.sh
    └── test-utils.sh
```

How to run this playbook
------------------------
```bash
ansible-playbook main.yml -i inventory/host.ini --extra-vars "aws_access_key=<your_access_key> aws_secret_key=<your_secrect_key>"
```
**I strongly recommend to set the aws keys as a command line argument to avoid any security issue writing thess credentials on files.**