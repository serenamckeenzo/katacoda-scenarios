Download and install Elasticsearch.

Depending on your environment, you can download the Elasticsearch rpm from the elastic website,
or use a package manager like yum or apt-get:

## Option 1: Download RPM from elastic.co and install manually

Use curl to download the desired version of Elasticsearch:

`curl https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.8.0-x86_64.rpm > elasticsearch.rpm`{{execute}}

Before we can install our local rpm we will need to install alien in the interactive shell.

`apt install alien`

And then we can use alien (or yum on RHEL machines) to install Elasticsearch:

`alien -i -v ./elasticsearch.rpm`

## Option 2: Install Elasticsearch using package manager

On Ubuntu we will be using apt-get to install Elasticsearch. If you want to use yum, you
will have to [configure yum to use the Elastic repository](https://www.elastic.co/guide/en/elasticsearch/reference/7.8/rpm.html#rpm-repo "Elastic Documentation").

Let's first [configure apt-get to use the Elastic repository](https://www.elastic.co/guide/en/elasticsearch/reference/7.8/deb.html#deb-repo "Elastic Documentation").

Download and install Elastic's public signing key:

`wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -`{{execute}}

Afterwards save the repository definition in apt sources:

`echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list`{{execute}}

Afterwards you're ready to use apt-get to install Elasticsearch:

`sudo apt-get update && sudo apt-get install elasticsearch=7.8.0`{{execute}}
