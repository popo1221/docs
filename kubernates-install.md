

- Need to install docker-compose(1.7.1+) by yourself first and run this script again.
```bash
$> sudo -E env "PATH=$PATH" ./install.sh
# or
$> sudo groupadd docker
$> sudo usermod -aG docker $USER
```

- Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?
```bash
$> sudo service docker stop
$> sudo nohup docker daemon -H tcp://0.0.0.0:2375 -H unix:///var/run/docker.sock &
```

- ERROR: for harbor-log  Cannot start service log: b'driver failed programming external connectivity on endpoint harbor-log (cbf3d6ca63d80d4ec6bff9d5eb4242e2c6426a80d2fe9f086adff190874d66b8): exec: "docker-proxy": executable file not found in $PATH'
```bash
$> cd /usr/libexec/docker/
$> sudo ln -s /usr/bin/libexec/docker/docker-proxy-current /usr/bin/docker-proxy 
```

- /usr/bin/docker-current: Error response from daemon: shim error: docker-runc not installed on system.
```bash
$> cd /usr/libexec/docker/
$> sudo ln -s /usr/libexec/docker/docker-runc-current /usr/bin/docker-runc
```

- Bind for 127.0.0.1:1514 failed: port is already allocated'
修改文件`docker-compose.yml`中：
- 127.0.0.1:1514:10514 ==> - "1514:10514"
