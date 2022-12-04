
## create user 

become postgres superuser and enter psql  
`sudo -u postgres psql`

then create new user 
```
CREATE DATABASE yourdbname;
CREATE USER youruser WITH ENCRYPTED PASSWORD 'yourpass';
GRANT ALL PRIVILEGES ON DATABASE yourdbname TO youruser;
```