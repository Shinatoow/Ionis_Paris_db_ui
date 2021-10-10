# B12db-UI

# Restore

First create volume to receive previous data:

```bash
docker volume create influxdb-storage
```

Launch a temporary ubuntu container to "flash" data from **influxdb.tar** directly inside the volume we created before

```bash
docker run --rm -v C:\Users\yourUser\yourPath\b12db-ui:/backup -v influxdb-storage:/data ubuntu bash -c "cd /data && tar xvf /backup/influxdb.tar"
```

Lauch influxdb

```bash
docker-compose up -d
```

# Backup

First stop influxdb

```bash
docker-compose down
```

Launch a temporary ubuntu container to "dump" data from **influxdb-storage** volume directly inside a tar named **influxdb.tar**

```bash
docker run --rm -v C:\Users\yourUser\yourPath\b12db-ui:/backup -v influxdb-storage:/data ubuntu bash -c "cd /data && tar cvf /backup/influxdb.tar ."
```

# First start

```bash
docker volume create influxdb-storage
docker-compose up -d
```
