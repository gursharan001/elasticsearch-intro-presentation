# Introduction

This is an introductory presentation about Elasticsearch, aimed at people who know little to nothing about it.

# Setup

Opened with the powerpoint, then ran though kibana.txt in kibana.

Basic Elasticsearch and kibana were installed on the local machine 
* Elasticsearch on localhost:9200
* Kibana at localhost:5601/app/sense

# Data Source

The data used for the presentation was setup as follows.

Source data was obtained from [Airplane Crashes Since 1908 on Kaggle](https://www.kaggle.com/saurograndi/airplane-crashes-since-1908)

Csv converted to json using [nodejs csvtojson](https://www.npmjs.com/package/csvtojson)

Json reformatted and bulk posted to elasticsearch, using [jq](https://stedolan.github.io/jq/)
```
cat AirplaneCrashes.json | jq -c '.[] | {"index": {"_index": "airplanecrash", "_type": "type1"}}, .' | curl -XPOST localhost:9200/_bulk --data-binary @-
```

# References

[On using jq with Elasticsearch](http://kevinmarsh.com/2014/10/23/using-jq-to-import-json-into-elasticsearch.html)

[Main Elasticsearch site](https://www.elastic.co)

[Use cases, including prominent Elasticsearch users](https://www.elastic.co/use-cases)

[Stack Overflow architectural overview, including Elasticsearch usage](http://nickcraver.com/blog/2016/02/17/stack-overflow-the-architecture-2016-edition/)

[REA and elasticsearch](https://www.elastic.co/elasticon/tour/2015/sydney/rea-group-elasticsearch-powers-real-estate-searches)

[Seek and elasticsearch](https://speakerdeck.com/elastic/seek-elasticsearch-from-hack-to-production)

[Mention of elasticsearch by domain](http://tech.domain.com.au/2015/04/chatops-at-domain-group/)

