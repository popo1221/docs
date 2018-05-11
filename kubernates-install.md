

- Need to install docker-compose(1.7.1+) by yourself first and run this script again.
```bash
$> sudo -E env "PATH=$PATH" ./install.sh
```

- Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?
```bash
$> sudo service docker stop
$> sudo nohup docker daemon -H tcp://0.0.0.0:2375 -H unix:///var/run/docker.sock &
```
