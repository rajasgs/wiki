/ [Home](index.md)

# How to install Vector on Ubuntu?


```
How to install vector?


curl -1sLf   ‘https://repositories.timber.io/public/vector/cfg/setup/bash.deb.sh’ | sudo -E bash

sudo apt-get install vector

verify:
vector --version

pre-requisite:
mkdir -p /var/lib/vector/
chmod 777 /var/lib/vector/ (give writing permission)



sudo nano ~/.vector/config/sc_deepad_dev.toml
	[sources.sc_deepad_dev_logs]
	type     = "file"
	include  = ["<ubuntu path of your .log file>"]

	[sinks.es_cluster]
	inputs   = ["sc_deepad_dev_logs"]
	type     = "elasticsearch"
	endpoint = "https://search-scrapercentral-dagcdizqvq5ppqke6wo7etojq4.us-east-2.es.amazonaws.com"

	  [sinks.es_cluster.bulk]
	  index    = "sc_deepad_dev-%Y-%m-%d"

	  [sinks.es_cluster.auth]
	  strategy = "<TBD>"
	  user     = "<TBD>"
	  password = "<TBD>"


How to run?
vector --config ~/.vector/config/sc_deepad_dev.toml

sudo service vector status

more info:
https://vector.dev/docs/setup/installation/package-managers/apt/
```