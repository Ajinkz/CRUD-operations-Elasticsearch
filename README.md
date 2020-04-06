# CRUD operations using Elasticsearch APIs

## Launch Elasticsearch service  

Open command prompt in administrative mode 
Type `elasticsearch`

In browser check this site: `http://localhost:9200` or use [curl](https://curl.haxx.se/)

![Check Elasticsearch](/images/1_check_elasticsearch.jpg)

## Check cluster heatlh status 

### GET /_cat/health?v&pretty 
http://localhost:9200/_cat/health?v&pretty 
![Check Elasticsearch](/images/2_health.jpg)
Format: ![Alt Text](url)

### GET /_cat/nodes?v&pretty 
http://localhost:9200/_cat/nodes?v&pretty 
![Check nodes](/images/3_nodes.jpg)
 
## Listing all indices 
GET /_cat/indices?v&pretty 
http://localhost:9200/_cat/indices?v&pretty 
![Check indices](/images/4_list_indices.jpg)


## Create an index (equivalent to creating a new database) 

PUT /index-name

`curl -XPUT "localhost:9200/products?&pretty"`
![Create index](/images/5_put_index.jpg)


##  Query a index/document 
Apart from curl. We also use Postman or YARC for handling API request
PUT /index-name/document-name/id

```
{ 
  “field”:”value”, 
    ... 
}
```
Id is optional, if not provided it will generate a unique id for this record


## Fetching  documents 

GET /products/mobile/1 
`curl -GET "localhost:9200/products/mobiles/1?pretty"`


### Getting partial documents 

`curl -GET "localhost:9200/products/mobiles/1?pretty&_source=false"`

`curl -GET "localhost:9200/products/mobiles/1?pretty&_source=name,reviews"`

## Updating documents 

### Updates using the _update API with "doc" 

`curl -XPOST -H "Content-Type: application/json" "localhost:9200/products/mobiles/2/_update?pretty" -d "{ \"doc\": { \"color\": \"black\"}}" `


## Deletion 

For deleting record
DELETE /index-name/document-name/id
  
`curl -XDELETE "localhost:9200/products/mobiles/2?pretty"`

For Removing index
DELETE /index-name

`curl –XDELETE “localhost:9200/orders”`
