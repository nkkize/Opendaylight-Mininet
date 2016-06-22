# Opendaylight-Mininet
Learning - Opendylight setup with mininet
Opendaylight is a Java based controller. First install java run-time environment on your machine

Install java
```
$ sudo add-apt-repository ppa:webupd8team/java -y
$ sudo apt-get update
$ sudo apt-get install oracle-java8-installer
$ sudo apt-get install oracle-java8-set-default
```
Install Mininet:
```
$ git clone git://github.com/mininet/mininet
$ cd mininet
$ ~/mininet/util/install.sh -a
Ping test
$ sudo mn --test pingall
```

Install Opendaylight Controller
```
$ wget https://nexus.opendaylight.org/content/groups/public/org/opendaylight/integration/distribution-karaf/0.4.0-Beryllium/distribution-karaf-0.4.0-Beryllium.tar.gz
Extract the downloaded file
$ sudo -xvzf distribution-karaf-0.4.0-Beryllium.tar.gz
```

Start Opendaylight
```
$ cd distribution-karaf-0.4.0-Beryllium
$ ./bin/karaf
```

Install required features
```
opendaylight-user@root> feature:install odl-restconf odl-mdsal-clustering odl-dlux-core odl-dlux-node odl-dlux-yangui odl-dlux-yangvisualizer odl-l2switch-all
```

Start mininet topology
```
$ sudo mn --controller=remote,ip=127.0.0.1 --mac --topo tree,3
```
Ping Test
```
$ mininet> pingall
```

View Topology and YangUI. Use username/password: admin/admin
```
localhost:8181/index.html
```
