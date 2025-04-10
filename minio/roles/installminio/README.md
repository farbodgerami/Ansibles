#### update and upgrade
sudo apt update
sudo apt upgrade
#### get de .deb file
wget https://dl.min.io/server/minio/release/linux-amd64/minio.deb
#### install the .deb file
sudo dpkg -i minio.deb
#### create group minio-user
sudo groupadd -r minio-user
#### create system user minio-user
sudo useradd -M -r -g minio-user minio-user
#### make directory for data
sudo mkdir /mnt/data
#### change the ownership of the dir
sudo chown minio-user:minio-user /mnt/data
#### put some of variables to a file
/etc/default/minio

```
MINIO_VOLUMES="/mnt/data"

MINIO_OPTS="--certs-dir /home/sammy/.minio/certs --console-address :9001"

MINIO_ROOT_USER=minioadmin

MINIO_ROOT_PASSWORD=minioadmin
```
#### start the service
sudo systemctl status minio