'''
sudo apt install mysql-server
'''
sudo mysql_secure_installation

y

1

'my_password'

'my_password'

y -> to accept password

y -> to remove anonymous user

y -> to disallow root login

y -> to remove test database

y -> to reload privilege tables


sudo mysql -u root

USE mysql;

UPDATE user SET plugin='mysql_native_password' WHERE User='root';

UPDATE mysql.user set authentication_string=PASSWORD('my_password') where 
user='root';

FLUSH PRIVILEGES;

quit

