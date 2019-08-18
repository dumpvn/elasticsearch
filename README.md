# elasticsearch

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
```
