# Task2-deploy-frontend-backend-dumblplay


INSTALASI INSTANCE BACKEND DAN DATABASE
- Membuat VM machine di AWS pilih launch instance -> pilih AMI ubuntu 18.04
![alt text](https://github.com/azhari7/Task2-deploy-frontend-backend-dumblplay/blob/main/Week%202/Aws-w2-install-instance.jpg)
- Pilih resource cpu yang dipakai disini memakai 1 core dan 1gb memory
![alt text](https://github.com/azhari7/Task2-deploy-frontend-backend-dumblplay/blob/main/Week%202/Aws-w2-02-choose-cpu.jpg)
- Konfigurasi networking auto assign-ip pilih disable ip public akan memakai elastic ip
![alt text](https://github.com/azhari7/Task2-deploy-frontend-backend-dumblplay/blob/main/Week%202/Aws-w2-03-choose-IP.jpg)
- Konfigurasi storage pilih default (8 GB)
![alt text](https://github.com/azhari7/Task2-deploy-frontend-backend-dumblplay/blob/main/Week%202/Aws-w2-04-choose-storage.jpg)
- Penambahan elastic IP pada database instance dan backend instance
![alt text](https://github.com/azhari7/Task2-deploy-frontend-backend-dumblplay/blob/main/Week%202/Aws-w2-05-elasticIP.jpg)


INSTALASI DATABASE MYSQL 5.7
- Download repository mysql dengan perintah wget 
![alt text](https://github.com/azhari7/Task2-deploy-frontend-backend-dumblplay/blob/main/Week%202/Aws-w2-06-install-database.jpg)
- konfigurasi package mysql dengan perintah sudo dpkg -i mysql-apt-config_0.8.15_1-all.deb
![alt text](https://github.com/azhari7/Task2-deploy-frontend-backend-dumblplay/blob/main/Week%202/Aws-w2-07-versi-database.jpg)
- update dan install mysql server 5.7 dengan sudo apt-get update -> sudo apt install mysql-server
![alt text](https://github.com/azhari7/Task2-deploy-frontend-backend-dumblplay/blob/main/Week%202/Aws-w2-08-install-database.jpg)
- Membuat database bernama dumbplay
![alt text](https://github.com/azhari7/Task2-deploy-frontend-backend-dumblplay/blob/main/Week%202/Aws-w2-09-create-databse.jpg)
- memberikan akses database dumbplay dari ip private backend instance
![alt text](https://github.com/azhari7/Task2-deploy-frontend-backend-dumblplay/blob/main/Week%202/Aws-w2-18-mysqlconfig.jpg)
- Konfigurasi pada my.cnf agar terkoneksi dari luar localhost dengan mengganti bind-address dengan 0.0.0.0
![alt text](https://github.com/azhari7/Task2-deploy-frontend-backend-dumblplay/blob/main/Week%202/Aws-w2-17-ipconfigbind.jpg)
- restart mysql 


INSTALASI BACKEND DUMBPLAY
- Instal ssh-key kemudian copy file id_rsa.pub pada github
![alt text](https://github.com/azhari7/Task2-deploy-frontend-backend-dumblplay/blob/main/Week%202/Aws-w2-10-sshkey.jpg)
- Clone git dumbplay 
![alt text](https://github.com/azhari7/Task2-deploy-frontend-backend-dumblplay/blob/main/Week%202/Aws-w2-11-gitclone.jpg)
- tambah repo node v 10 
![alt text](https://github.com/azhari7/Task2-deploy-frontend-backend-dumblplay/blob/main/Week%202/Aws-w2-12-add%20repo%20node.jpg)
- install nodejs dengan perintah sudo apt-get install -y nodejs
![alt text](https://github.com/azhari7/Task2-deploy-frontend-backend-dumblplay/blob/main/Week%202/Aws-w2-13-install%20node.jpg)
- install sequelize dengan perintah sudo npm i -g sequelize-cli
![alt text](https://github.com/azhari7/Task2-deploy-frontend-backend-dumblplay/blob/main/Week%202/Aws-w2-14-install%20sequelize.jpg)
- masuk ke folder backend ketikan perintah "copy .env-copy .env" kemudian "npm install"
![alt text](https://github.com/azhari7/Task2-deploy-frontend-backend-dumblplay/blob/main/Week%202/Aws-w2-15-cp%20env%26npm%20install.jpg)
- konfigurasi config.js database dengan menyesuaikan user, password, database, host dan dialect pada development
![alt text](https://github.com/azhari7/Task2-deploy-frontend-backend-dumblplay/blob/main/Week%202/Aws-w2-16-config.jsdb.jpg)
- ketikan perintah sequelize db:migrate
![alt text](https://github.com/azhari7/Task2-deploy-frontend-backend-dumblplay/blob/main/Week%202/Aws-w2-19-dbmigrate.jpg)
- Deploy backend dengan pm2
![alt text](https://github.com/azhari7/Task2-deploy-frontend-backend-dumblplay/blob/main/Week%202/Aws-w2-21-pm2%20exe.jpg)
- Pada server reverse proxy buat konfigurasi api.azhari.instructype.com yang akan di redirect ke ip private backend port 5000
![alt text](https://github.com/azhari7/Task2-deploy-frontend-backend-dumblplay/blob/main/Week%202/Aws-w2-25-proxybackend.jpg)
- restart nginx

- testing api backend dengan postman
![alt text](https://github.com/azhari7/Task2-deploy-frontend-backend-dumblplay/blob/main/Week%202/Aws-w2-26-testing%20api.jpg)


DEPLOY FRONTEND DUMBPLAY
- Konfigurasi api.js pada folder frontend/src/config
![alt text](https://github.com/azhari7/Task2-deploy-frontend-backend-dumblplay/blob/main/Week%202/Aws-w2-23-frontentobackend.jpg)
- Deploy frontend dengan pm2
![alt text](https://github.com/azhari7/Task2-deploy-frontend-backend-dumblplay/blob/main/Week%202/Aws-w2-24-frontenddeploy.jpg)
