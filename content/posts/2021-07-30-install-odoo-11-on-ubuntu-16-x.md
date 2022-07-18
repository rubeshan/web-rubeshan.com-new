---
date: 2021-08-08 11:22:45
title: Install Odoo 11 on Ubuntu 16.x
subtitle: ""
description: Odoo is one of the fastest growing ERP out there. Here is the
  installation steps for you to setup locally on your server.
image: https://ucarecdn.com/5760ee62-dde9-4075-9982-a609740a6582/-/resize/800x600/new-size_odoo.jpeg
optimized_image: https://ucarecdn.com/5760ee62-dde9-4075-9982-a609740a6582/-/resize/800x600/new-size_odoo.jpeg
category: tutorials
tags:
  - odoo
  - install
  - python
author: Ruben
paginate: false
layout: post
draft: true
featured: false
---

Odoo is a suite of business management software tools including, for example, CRM, e-commerce, billing, accounting, manufacturing, warehouse, project management, and inventory management. The Community version is a libre software, licensed under the GNU LGPLv3. [Wikipedia]

Steps to Install Odoo 11 on Ubuntu 16.04

Below are the steps to install Odoo 11 on your Ubuntu Server/Machine.

Let's begin.

Open the terminal and execute below commands step-by-step.

#### Step 1: Update apt source list

```
sudo apt-get update
```

#### Step 2: Install Updates

```
sudo apt-get -y upgrade
```

Note: The -y flag will confirm that we are agreeing for all items to be installed.

Step 3: Install Python Dependencies for Odoo 11

```
sudo apt-get install python3-pip
```

#### Step 4: Install Dependencies Using pip3

```
pip3 install Babel decorator docutils ebaysdk feedparser gevent greenlet html2text
Jinja2 lxml Mako MarkupSafe mock num2words ofxparse passlib Pillow psutil
psycogreen psycopg2 pydot pyparsing PyPDF2 pyserial python-dateutil python-openid
pytz pyusb PyYAML qrcode reportlab requests six suds-jurko vatnumber vobject
Werkzeug XlsxWriter xlwt xlrd
```

#### Step 5: Odoo Web Dependencies

```
sudo apt-get install -y npm
sudo ln -s /usr/bin/nodejs /usr/bin/node
sudo npm install -g less less-plugin-clean-css
sudo apt-get install node-less
```

#### Step 6: Install PostgreSQL 9.6+

```
sudo apt-get install python-software-properties
sudo vim /etc/apt/sources.list.d/pgdg.list
```

#### add a line for the repository

```
deb http://apt.postgresql.org/pub/repos/apt/ xenial-pgdg main
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
sudo apt-get update
sudo apt-get install postgresql-9.6
```

#### Step 7: Create Database User for Odoo

```
sudo su postgres
cd
createuser -s odoo
createuser -s ubuntu_user_name
exit
```

#### Step 8: Create Odoo User and Group

```
sudo adduser --system --home=/opt/odoo --group odoo
```

#### Step 9: Install Gdata

```
cd /opt/odoo
sudo wget https://pypi.python.org/packages/a8/70/bd554151443fe9e89d9a934a7891aaffc63b9cb5c7d608972919a002c03c/gdata-2.0.18.tar.gz
sudo tar zxvf gdata-2.0.18.tar.gz
sudo chown -R odoo: gdata-2.0.18
sudo -s
cd gdata-2.0.18/
python setup.py install
exit
```

#### Step 10: Download Odoo 11

Go to the url : URL : “https://github.com/odoo/odoo/tree/11.0″
Download the Zipped File
Transfer the file to /opt/odoo directory on server through ftp. 
or 
Follow the steps below

```
cd /opt/odoo
sudo apt-get install git
sudo su - odoo -s /bin/bash
git clone https://www.github.com/odoo/odoo --depth 1 --branch 11.0 --single-branch
```

#### Step 11: Create Odoo Log File

```
sudo mkdir /var/log/odoo
sudo chown -R odoo:root /var/log/odoo
```

#### Step 12: Edit Odoo configuration file

```
sudo vim /etc/odoo.conf
```

Copy and paste below content in config file  and write correct addons paths

```
[options]
; This is the password that allows database operations:
; admin_passwd = admin
db_host = False
db_port = False
db_user = odoo
db_password = False
logfile = /var/log/odoo/odoo-server.log
addons_path = /opt/odoo/addons,/opt/odoo/odoo/addons
```

Save and Exit the file. Now run the below command on terminal to grant ownership.

```
sudo chown odoo: /etc/odoo.conf
```

#### Step 13: WKHTMLTOPDF ( Supported Version 0.12.1 ) for Odoo

```
sudo wget https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.1/wkhtmltox-0.12.1_linux-trusty-amd64.deb
sudo dpkg -i wkhtmltox-0.12.1_linux-trusty-amd64.deb
sudo cp /usr/local/bin/wkhtmltoimage /usr/bin/wkhtmltoimage
sudo cp /usr/local/bin/wkhtmltopdf /usr/bin/wkhtmltopdf
```

#### Step 14: Start Odoo Server

```
cd /opt/odoo/odoo
./odoo-bin
```

#### Step 15: Go to your web browser to access Odoo 11

http://localhost:8069

and Press Enter.