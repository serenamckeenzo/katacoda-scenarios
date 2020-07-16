Kibana can be installed in the same way Elastisearch was - either downloading manually or via a package manager.

## Install Kibana

### Option 1: Download manually

`curl https://artifacts.elastic.co/downloads/kibana/kibana-7.8.0-x86_64.rpm > kibana.rpm`{{execute}}

`alien -i -v ./kibana.rpm`{{execute}}

### Option 2: Use package manager

As we have already configured the Elastic repository in the previous step we can simply install Kibana with:

`sudo apt-get install kibana=7.8.0`{{execute}}

## Start Kibana

Again, we can use systemctl commands to start and check Kibana.

`systemctl start kibana`{{execute}}

`systemctl status kibana`{{execute}}

By default Kibana binds to port 5601 for HTTP traffic which we can verify with the netsat command:

`netstat -tulpn | grep '5601'`{{execute interrupt}}

The port can be changed in `etc/kibana/kibana.yml`{{open}} under the **Network** settings.
