# seastar_example

build 
```
docker pull scylladb/scylla-build-dependencies-docker:fedora-28

docker run -d --name scylla -it scylladb/scylla-build-dependencies-docker:fedora-28 bash

build seastar

1) git clone https://github.com/scylladb/seastar.git

2) cd seastar

3) git submodule update --init --recursive

4) sudo ./install-dependencies.sh

5)
./configure.py --compiler=g++ --mode=release

6) ninja -j10

build server:
g++ -std=c++11  -I /seastar -L /usr/lib64  `pkg-config --cflags --libs /seastar/build/release/seastar.pc` -o server server.cc

build client:
g++ -std=c++11  -I /seastar -L /usr/lib64  `pkg-config --cflags --libs /seastar/build/release/seastar.pc` -o client client.cc

```



run server

```
./server --port=13001 --smp=12
```

run client

```
./client --smp=12 --server=your_ip:13001 --conn=12
```


