In this step we will start the Elasticsearch service and ensure it's running correctly.

## Configure Elasticsearch

On most instances the default configuration of Elasticsearch would serve you well on an initial startup - however
within this training environment we will need to set Elasticsearch's memory requirements lower to avoid out of memory errors.

We can do this easily by modifying the initial and maximum Java heap size - in the `/etc/` folder open `elasticsearch/jvm.options`{{open}}

## Start the Elasticsearch service

Using systemctl commands we can check the status and start up the Elasticsearch service:

`systemctl start elasticsearch`{{execute}}

As we're using the default settings, Elasticsearch should start up without problems:

`systemctl status elasticsearch`{{execute}}

By default Elasticsearch binds to two ports: 9200 for HTTP traffic and 9300 for transport layer traffic.  
We can confirm these ports using the netsat command:

`netstat -tulpn | grep '9200\|9300'`{{execute interrupt}}


Within the `/etc/` folder, open `elasticsearch/elasticsearch.yml`{{open}} and navigate to the below **Network** settings:

```
# Set the bind address to a specific IP (IPv4 or IPv6):
#
#network.host: 192.168.0.1
#
# Set a custom port for HTTP:
#
#http.port: 9200
#
# For more information, consult the network module documentation.
```

As you can see by default these settings are commented out and thus Elasticsearch is binding to localhost
on ports 9200 and 9300 (as confirmed by the netstat command above). <br><br>
The default yaml tells you how to change the http port if needed, however there are even more granular settings you can use described in the [documentation](https://www.elastic.co/guide/en/elasticsearch/reference/current/modules-network.html "Network settings").

`http.port: 9200`

However to change the transport port you'll need to refer to the [documentation](https://www.elastic.co/guide/en/elasticsearch/reference/current/modules-transport.html "Transport settings") to find the below setting:

`transport.port: 9300`

However for our purposes we will keep the default settings.
