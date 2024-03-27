# LocalDOH
DNS over HTTPS for Local area Network

This application is specifically helpful when you are using service like pi-hole or adgaurd and you want to encrypt the dns request in your local network. This can also be used if you want to host your own dns server, this application can be used on top of your dns provider application to provide DNS-over-HTTPS(DOH) facility.

Network Diagrams for both the cases are provided below


## Setup on Linux


### 1.1) Copy this repository

`$ git clone https://github.com/PA-Games-SSDDR/LocalDOH.git`

###  1.2) Create venv with python packages in linux

```
# In LocalDOH directory
$ python -m venv venv
$ source ./venv/bin/activate
$(venv) python -m pip install -r requirements.txt
```

### 1.3) add conf file for your local domain

Copy `localdoh.local.conf` to `/etc/nginx/sites-enabled` making required changes to add your own ssl keys and making domain changes as required.
Then make it available `ln -s /etc/nginx/sites-available/localdoh.local.conf /etc/nginx/sites-enabled/localdoh.local.conf`

### 1.4) create a service so that it always runs

Copy `localdoh.service` to `/etc/systemd/system/` making changes as per your requirement. then enable and start the service and check its status.
```
$ sudo systemctl start localdoh
$ sudo systemctl enable localdoh
$ sudo systemctl status localdoh
```


