Kibana can be installed in the same way Elastisearch was - either downloading manually or via a package manager.

## Install Kibana

**Option 1: Download manually**

`curl https://artifacts.elastic.co/downloads/kibana/kibana-7.8.0-x86_64.rpm > kibana.rpm`{{execute}}

`alien -i -v ./kibana.rpm`{{execute}}

**Option 2: Use package manager**

As we have already configured the Elastic repository in the previous step we can simply install Kibana with:

`sudo apt-get install kibana=7.8.0`{{execute}}

## Configure Kibana

Although Kibana start up with the default settings, in order to be able to hit the GUI we will need to change Kibana's bind settngs.

Looking in `/etc/`, `kibana/kibana.yml`{{open}} you will find the following description:

```
# Specifies the address to which the Kibana server will bind. IP addresses and host names are both valid values.
# The default is 'localhost', which usually means remote machines will not be able to connect.
# To allow connections from remote users, set this parameter to a non-loopback address.
#server.host: "localhost"
```

To allow ourselves to connect to the Kibana server through Katacoda, we'll have to bind the service to its IP address.

First let's check the IP address of our server:

`ip addr show`{{execute}}

You should see a similar output:
<pre>
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: ens3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 02:42:ac:11:00:4e brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.78/16 brd 172.17.255.255 scope global ens3
       valid_lft forever preferred_lft forever
    inet6 fe80::42:acff:fe11:4e/64 scope link
       valid_lft forever preferred_lft forever
</pre>

In this line you can see your current IP address: `inet 172.17.0.78/16 brd 172.17.255.255 scope global ens3`
which in this example is `172.17.0.78`.

<pre class="file" data-filename="kibana/kibana.yml" data-target="insert"  data-marker='#server.host: "localhost"'>server.host: "[your ip address]"</pre>

## Start Kibana

Again, we can use systemctl commands to start and check Kibana.

`systemctl start kibana`{{execute}}

`systemctl status kibana`{{execute}}

By default Kibana binds to port 5601 for HTTP traffic which we can verify with the netsat command:

`netstat -tulpn | grep '5601'`{{execute interrupt}}

The port can be changed in `/etc/`, `kibana/kibana.yml`{{open}} with the `server.port: 5601` setting:

```
# Kibana is served by a back end server. This setting specifies the port to use.
#server.port: 5601
```

As you can see, the whole of the Kibana configuration is commented out meaning that our service is
using the default values - for now we'll keep it like that.
