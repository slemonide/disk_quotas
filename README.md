## Create directory to store disks
```
mkdir dev
```

## Create directory to store mount points
```
mkdir mnt
```

## Create 3 disks of size 1G each
```
dd if=/dev/zero of=dev/1 count=1024 bs=1048576
dd if=/dev/zero of=dev/2 count=1024 bs=1048576
dd if=/dev/zero of=dev/3 count=1024 bs=1048576
```

## Create file system on them
```
mkfs.ext4 dev/1
mkfs.ext4 dev/2
mkfs.ext4 dev/3
```

## Mount these 3 disks
```
sudo mount dev/1 mnt/1
sudo mount dev/2 mnt/2
sudo mount dev/3 mnt/3
```

## Test that these are indeed 1G in size
```
df -h 
```


## Now can bind mount them to docker
```
    volumes:
      - ./mnt/1:/mnt/1
      - ./mnt/2:/mnt/2
      - ./mnt/3:/mnt/3
```
