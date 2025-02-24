# Lab 1: Containerization

## 1. Docker command to create and run a container named `dbserver-mysql-nairobi`

Use the `customized-ubuntu:1.0` image to create a container named `dbserver-mysql-nairobi`. The command should map the container’s port 3306 to the host’s port 3309.

```dockerfile
Specify your commands here
# Build the image
docker build -t customized-ubuntu:1.0 images/ubuntu
# Run the container
docker run -d --name dbserver-mysql-nairobi -p 3309:3306 customized-ubuntu:1.0 tail -f /dev/null
# Verify running container 
docker ps
```

## 2. MySQL Server and MySQL Client Installation in Ubuntu

```shell
Specify your commands here
# Access the container
docker exec -it dbserver-mysql-nairobi bash
# Update package lists
apt-get update
# Install MySQL Server and Client
apt-get install -y mysql-server mysql-client
# Start MySQL service
service mysql start
```

## 3. Login using the MySQL Client and Change the MySQL Root Password

```sql
Specify your commands here
# Log in to MySQL
mysql -u root -p
```
Inside the MySQL shell, run:

```sql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '5trathmore';
FLUSH PRIVILEGES;
EXIT;
```
```sh
# Commit the container state
docker commit dbserver-mysql-nairobi dbserver-mysql-nairobi
# Stop and start the container
docker stop dbserver-mysql-nairobi
docker start dbserver-mysql-nairobi
# Reattach to the container
docker attach dbserver-mysql-nairobi
# Start MySQL service
service mysql start
# Connect to MySQL
mysql -u root -p
```



