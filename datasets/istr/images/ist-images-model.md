## images-sample.json

### PyTransforms
#### _ad_crawl_uri_
From column: _ad_url_
>``` python
return getCacheBaseUrl() + "page/"+get_url_hash(getValue("ad_url"))+"/"+getValue("ad_timestamp") + "/processed"
```

#### _image_uri_
From column: _url_
>``` python
return getCacheBaseUrl() + "image/"+get_url_hash(getValue("url"))+"/"+getValue("ad_timestamp") + "/processed"
```

#### _image_snapshot_uri_
From column: _image_uri_
>``` python
return getCacheBaseUrl() + "image/"+get_url_hash(getValue("url"))+"/"+getValue("ad_timestamp") + "/raw"
```

#### _modtime_iso_
From column: _modtime_
>``` python
return iso8601date(getValue("modtime"))
```

#### _database_id_
From column: _modtime_iso_
>``` python
if getValue("image_uri"):
  return getValue("id")
return ''
```


### Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| _ad_crawl_uri_ | `uri` | `schema:WebPage1`|
| _database_id_ | `memex:databaseId` | `prov:Activity1`|
| _image_snapshot_uri_ | `memex:snapshotUri` | `schema:ImageObject1`|
| _image_uri_ | `uri` | `schema:ImageObject1`|
| _importtime_ | `prov:generatedAtTime` | `schema:ImageObject1`|
| _location_ | `memex:cacheUrl` | `schema:ImageObject1`|
| _modtime_iso_ | `prov:endedAtTime` | `prov:Activity1`|
| _url_ | `schema:url` | `schema:ImageObject1`|


### Links
| From | Property | To |
|  --- | -------- | ---|
| `schema:ImageObject1` | `schema:mentions` | `prov:Activity1`|
| `schema:ImageObject1` | `prov:wasGeneratedBy` | `xsd:http://memexproxy.com/data/software/extractor/ist/ist-images-database`|
| `schema:WebPage1` | `memex:hasImagePart` | `schema:ImageObject1`|