
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


(If Permission Denied then Own .ssh then try again to Generate SSH Keys)
Syntax:- sudo chown -R user_name .ssh
Example:- sudo chown -R raj .ssh

```


- Open Public SSH Keys then copy the key
```cat ~/.ssh/id_ed25519.pub```
- Go to Your Github Repo-Click SETTING < DEPLOY KEYS < ADD DEPLOY KEYS and Paste Copied SSH Public Key then Click on ADD KEY.

- Verify the Connection, Go to Your Server Terminal then run below
```ssh -T git@github.com
// OR
ssh -vT git@github.com```




## Clone Project 

- You may get an error git @ github.com: Permission denied (publickey) If you will try to clone it directly on Web Server Public Folder /var/www So we will clone github repo in User's Home Directory then Move it to Web server Public Directory

- Using SSH Path It requires to setup SSH Key on Github

```
Syntax:- git clone ssh_repo_path
Example:- git clone git@github.com:geekyshow1/miniblog.git
```


### Move Project Folder to Web Server public directory

```
Syntax:- sudo mv project_folder_name /var/www
Example:- sudo mv miniblog /var/www

- Go to Your Project Directory

Syntax:- cd /var/www/project_folder_name
Example:- cd /var/www/miniblog

- Create Virtual env
Syntax:- virtualenv env_name
Example:- virtualenv mb

- Activate Virtual env
Syntax:- source virtualenv_name/bin/activate
Example:- source mb/bin/activate

- Install Dependencies
pip install -r requirements.txt

```

# Apache2 work
### Create Virtual Host File
```nano /etc/apache2/sites-available/your_domain.conf```

- Add Following Code in Virtual Host File


```
<VirtualHost *:80>
    ServerName www.example.com
    ServerAdmin contact@example.com
    #Document Root is not required
    #DocumentRoot /var/www/project_folder_name
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
    
    Alias /static /var/www/project_folder_name/static
    <Directory /var/www/project_folder_name/static>
        Require all granted
    </Directory>
    
    Alias /media /var/www/project_folder_name/media
    <Directory /var/www/project_folder_name/media>
        Require all granted
    </Directory>
    
    <Directory /var/www/project_folder_name/Inner_project_folder_name>
        <Files wsgi.py>
            Require all granted
        </Files>
    </Directory>
    
    WSGIDaemonProcess any_name python-home=/var/www/project_folder_name/myprojectenv python-path=/var/www/project_folder_name
    WSGIProcessGroup any_name
    WSGIScriptAlias /  /var/www/project_folder_name/inner_project_folder_name/wsgi.py
</VirtualHost>
```

- Check Configuration is correct or not
```sudo apache2ctl configtest```















