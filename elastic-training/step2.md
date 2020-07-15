In this step we will start the Elasticsearch service and ensure it's running correctly.

## Start the Elasticsearch service

Using systemctl commands we can check the status and start up the Elasticsearch service:

`systemctl start elasticsearch`{{execute}}

As we're using the default settings, Elasticsearch should start up without problems:

`systemctl status elasticsearch`{{execute}}

By default Elasticsearch binds to two ports: 9200 for HTTP traffic and 9300 for transport layer traffic. /n
We can confirm these ports using the netsat command:

`netstat -tulpn | grep '9200\|9300'`{{execute interrupt}}

If needed you can change these ports in the elasticsearch.yml with the below settings:

`transport.port: 9300`

and

`network.port: 9200`

Open `/etc/elasticsearch/elasticsearch.yml`{{open}} and navigate to the **Network** settings

However for our purposes we will keep the default settings.
