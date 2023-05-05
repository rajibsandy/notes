

- For Oracal Cloud please use iptables

```
$ sudo iptables -I INPUT 6 -m state --state NEW -p tcp --dport 80 -j ACCEPT
$ sudo iptables -I INPUT 6 -m state --state NEW -p tcp --dport 443 -j ACCEPT
$ sudo netfilter-persistent save

````
### Note:- Run Below Commands on Your Remote Server Linux Machine or VPS, Not on Your Local Windows Machine
  - Verify that all required softwares are installed
  
  - If Required Softwares and Modules are not Installed then Install them:
  
```
sudo apt install apache2
sudo apt install python
sudo apt install libapache2-mod-wsgi-py3
sudo apt install python3-pip
sudo apt install git

apache2 -v
python --version
apache2ctl -M
pip --version
git --version
  
```
- python -c "import sqlite3; print(sqlite3.sqlite_version)"








- On Local Windows Machine, Goto Your Project Folder then follow below instruction:
- Create a folder in your root project directory then move database file inside this created directory e.g. mbdb/db.sqlite3
- Open settings.py file then change sqlite db file path as it is now inside folder



```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'mbdb/db.sqlite3',
    }
}
```
