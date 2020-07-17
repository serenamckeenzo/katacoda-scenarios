Metricbeat agents can be installed in the same way Elastisearch was - either downloading manually or via a package manager.

## Install Kibana

**Option 1: Download manually**

`curl https://artifacts.elastic.co/downloads/metricbeat/metricbeat-7.8.0-x86_64.rpm > metricbeat.rpm`{{execute}}

`alien -i -v ./metricbeat.rpm`{{execute}}

**Option 2: Use package manager**

As we have already configured the Elastic repository in the previous step we can simply install the agent with:

`sudo apt-get install metricbeat=7.8.0`{{execute}}

To avoid compatibility issues, make sure you always use the same version of the various Elastic stack components.

## Check Metricbeat configuration

## Start Metrcibeat

Again, we can use systemctl commands to start and check the beat agent.

`systemctl start metricbeat`{{execute}}

`systemctl status metricbeat`{{execute}}

Opening the Kibana frontend, you should now see the data from the agent.
