# elasticsearch

http://localhost:9200

## installing

### debian

```bash
wget https://download.elastic.co/elasticsearch/elasticsearch/elasticsearch-2.0.0.deb
sudo dpkg -i elasticsearch-2.0.0.deb
sudo update-rc.d elasticsearch defaults 95 10
```

### centos & redhat

```bash
wget https://download.elastic.co/elasticsearch/elasticsearch/elasticsearch-2.0.0.rpm
sudo rpm -i elasticsearch-2.0.0.rpm
sudo systemctl daemon-reload
sudo systemctl enable elasticsearch.service

sudo service elasticsearch start
sudo service elasticsearch status
```

### plugins

https://github.com/mobz/elasticsearch-head

```bash
sudo /usr/share/elasticsearch/bin/plugin -install mobz/elasticsearch-head
sudo service elasticsearch restart
http://localhost:9200/_plugin/head
```

https://github.com/bleskes/sense
http://localhost:5601/app/sense

## indexes

```bash
curl -XPUT 'localhost:9200/books/'
```

## documents

```bash
curl -XPUT 'localhost:9200/books/elasticsearch/1' -d '{
    "name":"Elasticsearch Essentials",
    "author":"Bharvi Dixit", 
    "tags":["Data Analytics","Text Search","Elasticsearch"],
    "content":"Added with PUT request"
}'

curl -XPOST 'localhost:9200/books/elasticsearch' -d '{
    "name":"Elasticsearch Essentials",
    "author":"Bharvi Dixit", 
    "tags":["Data Anlytics","Text Search","Elasticsearch"],
    "content":"Added with POST request"
    }'

curl -XGET 'localhost:9200/books/elasticsearch/1'?pretty
curl -XGET 'localhost:9200/books/elasticsearch/1'?_source=name,author
```


```bash
curl -XPUT 'localhost:9200/books/elasticsearch/1' -d '{
    "name":"Elasticsearch Essentials",
    "author":"Bharvi Dixit", 
    "tags":["Data Analytics","Text Search","Elasticsearch"],
    "content":"Updated document",
    "publisher":"pact-pub"
}'

curl -XPOST 'localhost:9200/books/elasticsearch/1/_update' -d '{
   "script":"ctx._source.updated_time=\"2019-08-18T00:00:00\""
}'

curl -XDELETE 'localhost:9200/books/elasticsearch/1'
curl –XPOST http://localhost:9200/_optimize?only_expunge_deletes=true'
```
