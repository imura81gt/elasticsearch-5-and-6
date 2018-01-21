start Elasticsearch & Kibana
===================================

```
$ docker-compose up
```

URL
====================================

| Products       | URL                     |
|:----           |:---                     |
|Elasticsearch 5 | http://localhost:19200/ |
|Kibana 5        | http://localhost:15601/ |
|Elasticsearch 6 | http://localhost:29200/ |
|Kibana 6        | http://localhost:25601/ |


Example
======================================

Testing Synonym Token Filter
---------------------------------------

> Synonym Token Filter
> https://www.elastic.co/guide/en/elasticsearch/reference/6.x/breaking_60_analysis_changes.html#_synonym_token_filter
> > In 6.0, Synonym Token Filter tokenizes synonyms with whatever tokenizer and token filters appear before it in the chain.

```
DELETE my_index

PUT my_index
{
  "settings": {
    "analysis": {
      "analyzer": {
        "ja_analyzer": { 
          "type": "custom",
          "char_filter": [
          ],
          "tokenizer": "kuromoji_tokenizer",
          "filter": [
            "lowercase",
            "asciifolding",
            "synonym"
          ]
        }
      },
      "filter" : {
        "synonym" : {
          "type" : "synonym",
          "synonyms" : [
            "i-pod, i pod, アイポッド, あいぽっど => ipod"
          ]
        }
      }
    }
  },
  "mappings": {
    "my_type": {
      "properties": {
        "my_text": {
          "type": "text",
          "analyzer": "ja_analyzer" 
        }
      }
    }
  }
}

GET my_index/_analyze 
{
  "analyzer": "ja_analyzer", 
  "text":     "I pod アイポッド あいぽっど"
}
```





