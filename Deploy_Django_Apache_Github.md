
# to Local project

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
- Save and Close settings.py file
- Open Terminal
- Activate Your virtual Env
- Create requirements.txt File

  ```pip freeze > requirements.txt```
  
- Deactivate Virtual Env

- Push your Poject to You Github Account as Private Repo.To Access Remote Server via SSH



# to VPS 

```
ssh ubuntu@140.238.241.**
sudo apt update 
sudo apt upgrade -y

```

- For Oracal Cloud please use iptables
```
sudo iptables -I INPUT 6 -m state --state NEW -p tcp --dport 80 -j ACCEPT
sudo iptables -I INPUT 6 -m state --state NEW -p tcp --dport 443 -j ACCEPT
sudo netfilter-persistent save

````
### Note:- Commands for VPS Server 
(Lets Verify all required softwares are installed or not , if not please Installed them one by one )

  
```
apache2 -v
python --version
apache2ctl -M
pip --version
git --version

sudo apt install apache2 -y
sudo apt install python -y
sudo apt install libapache2-mod-wsgi-py3
sudo apt install python3-pip -y
sudo apt install git -y

- SQLite is Included with Python
  python -c "import sqlite3; print(sqlite3.sqlite_version)"
  
```
- Install virtualenv

```
pip list
sudo pip install virtualenv
sudo service apache2 status

```

- Make Connection between vpsr &  Github------ via SSH Key
- Generate SSH Keys

```
ssh-keygen -t ed25519 -C "your_email@example.com"


- If Permission Denied then Own .ssh then try again to Generate SSH Keys
Syntax:- sudo chown -R user_name .ssh
Example:- sudo chown -R raj .ssh



```























