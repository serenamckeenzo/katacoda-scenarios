In this step we will ensure Elasticsearch and Kibana are connected and communicating correctly.

## Check Elasticsearch config

In the `/etc/` folder, open `elasticsearch/elasticsearch.yml`{{open}} and navigate to **Kibana settings**. <br><br>

Curl Kibana to confirm the service is listening:

`curl localhost:5601`{{execute}}

## Check Kibana config

In the `/etc/` folder, open `kibana/kibana.yml`{{open}} and navigate to **Elasticsearch settings**. <br><br>

Though Elastic takes care to align the configurations of its services, Kibana and Elasticsearch are still separate
software so pay attention to the settings syntax.

Curl Elasticserach to confirm the service is listening:

`curl localhost:9200`{{execute}}

## Check logs

Tail the Kibana and Elasticsearch logs and confirm the connection has been established successfully.
As we're using the default settings, the stack should connect up without intervention.

`tail logs` {{execute interrupt}}

you should see:

## Open Kibana

The Kibana UI tab should now take you to the Kibana frontend.
