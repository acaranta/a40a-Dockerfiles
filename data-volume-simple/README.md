data-volume-simple
==========

Simple data-volume, with a volume mounted on /data

Build :
```
docker build -t data-volume .
```
Create the data volume and some data
```
docker run -t -i --name datavol data-volume /bin/bash
#cd /data
#dd if=/dev/urandom of=bigfile bs=1024 count=102400
#ls -l /data
total 102400
-rw-r--r-- 1 root root 104857600 Sep  5 06:48 bigfile
#exit
```

Launch a test, mounting the created data volume and check if the data is here
```
docker run -t -i --name datavol2 --volumes-from=datavol data-volume /bin/bash
#ls /data
total 102400
-rw-r--r-- 1 root root 104857600 Sep  5 06:48 bigfile
```


