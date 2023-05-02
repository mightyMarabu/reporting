## query the sentinel api
* make a request
* search the result
* get download link
* download and save file



```python
#sentinel API
import requests
#LatLng = ('37.30488,01.85034') # Ngurunit
#LatLng = ('37.898626114941905,2.27305876687853') # near Marsabit
footprint = 'POLYGON((37.32548632535571 1.8491098129258177,38.06615104713074 1.8491098129258177,38.06615104713074 2.582527953220037,37.32548632535571 2.582527953220037,37.32548632535571 1.8491098129258177))'
#prodType = 'SLC'
prodType = 'S2MSI2A' #,S2MSI1C, S2MS2Ap

API = 'https://scihub.copernicus.eu/dhus/search?q=ingestiondate:[NOW-5DAY%20TO%20NOW]%20AND%20producttype:'+prodType+'%20AND%20footprint:"Intersects('+footprint+')"&%20rows=100&start=0&format=json'

from requests.auth import HTTPBasicAuth

r = requests.get(API,auth=('sebastiannormann', 'Goatscanfly_2022'))
print(r)
```

    <Response [200]>



```python
#r.headers['content-type']
#'application/json; charset=utf8'

searchResult = r.json()
searchResult
```




    {'feed': {'xmlns:opensearch': 'http://a9.com/-/spec/opensearch/1.1/',
      'xmlns': 'http://www.w3.org/2005/Atom',
      'title': 'Sentinels Scientific Data Hub search results for: ingestiondate:[NOW-5DAY TO NOW] AND producttype:S2MSI2A AND footprint:"Intersects(POLYGON((37.32548632535571 1.8491098129258177,38.06615104713074 1.8491098129258177,38.06615104713074 2.582527953220037,37.32548632535571 2.582527953220037,37.32548632535571 1.8491098129258177)))"',
      'subtitle': 'Displaying 1 results. Request done in 0.021 seconds.',
      'updated': '2023-05-02T08:04:22.502Z',
      'author': {'name': 'Sentinels Scientific Data Hub'},
      'id': 'https://scihub.copernicus.eu/dhus/search?q=ingestiondate:[NOW-5DAY TO NOW] AND producttype:S2MSI2A AND footprint:"Intersects(POLYGON((37.32548632535571 1.8491098129258177,38.06615104713074 1.8491098129258177,38.06615104713074 2.582527953220037,37.32548632535571 2.582527953220037,37.32548632535571 1.8491098129258177)))"',
      'opensearch:totalResults': '1',
      'opensearch:startIndex': '0',
      'opensearch:itemsPerPage': '10',
      'opensearch:Query': {'role': 'request',
       'searchTerms': 'ingestiondate:[NOW-5DAY TO NOW] AND producttype:S2MSI2A AND footprint:"Intersects(POLYGON((37.32548632535571 1.8491098129258177,38.06615104713074 1.8491098129258177,38.06615104713074 2.582527953220037,37.32548632535571 2.582527953220037,37.32548632535571 1.8491098129258177)))"',
       'startPage': '1'},
      'link': [{'rel': 'self',
        'type': 'application/json',
        'href': 'https://scihub.copernicus.eu/dhus/search?q=ingestiondate:[NOW-5DAY TO NOW] AND producttype:S2MSI2A AND footprint:"Intersects(POLYGON((37.32548632535571 1.8491098129258177,38.06615104713074 1.8491098129258177,38.06615104713074 2.582527953220037,37.32548632535571 2.582527953220037,37.32548632535571 1.8491098129258177)))"&start=0&rows=10&format=json'},
       {'rel': 'first',
        'type': 'application/json',
        'href': 'https://scihub.copernicus.eu/dhus/search?q=ingestiondate:[NOW-5DAY TO NOW] AND producttype:S2MSI2A AND footprint:"Intersects(POLYGON((37.32548632535571 1.8491098129258177,38.06615104713074 1.8491098129258177,38.06615104713074 2.582527953220037,37.32548632535571 2.582527953220037,37.32548632535571 1.8491098129258177)))"&start=0&rows=10&format=json'},
       {'rel': 'last',
        'type': 'application/json',
        'href': 'https://scihub.copernicus.eu/dhus/search?q=ingestiondate:[NOW-5DAY TO NOW] AND producttype:S2MSI2A AND footprint:"Intersects(POLYGON((37.32548632535571 1.8491098129258177,38.06615104713074 1.8491098129258177,38.06615104713074 2.582527953220037,37.32548632535571 2.582527953220037,37.32548632535571 1.8491098129258177)))"&start=0&rows=10&format=json'},
       {'rel': 'search',
        'type': 'application/opensearchdescription+xml',
        'href': 'opensearch_description.xml'}],
      'entry': {'title': 'S2A_MSIL2A_20230428T073611_N0509_R092_T37NCC_20230428T110612',
       'link': [{'href': "https://scihub.copernicus.eu/dhus/odata/v1/Products('f0223da2-d13f-40a2-b09a-e8d10a016ccb')/$value"},
        {'rel': 'alternative',
         'href': "https://scihub.copernicus.eu/dhus/odata/v1/Products('f0223da2-d13f-40a2-b09a-e8d10a016ccb')/"},
        {'rel': 'icon',
         'href': "https://scihub.copernicus.eu/dhus/odata/v1/Products('f0223da2-d13f-40a2-b09a-e8d10a016ccb')/Products('Quicklook')/$value"}],
       'id': 'f0223da2-d13f-40a2-b09a-e8d10a016ccb',
       'summary': 'Date: 2023-04-28T07:36:11.024Z, Instrument: MSI, Satellite: Sentinel-2, Size: 1011.32 MB',
       'ondemand': 'false',
       'date': [{'name': 'generationdate', 'content': '2023-04-28T11:06:12Z'},
        {'name': 'beginposition', 'content': '2023-04-28T07:36:11.024Z'},
        {'name': 'endposition', 'content': '2023-04-28T07:36:11.024Z'},
        {'name': 'ingestiondate', 'content': '2023-04-28T13:06:47.279Z'}],
       'int': [{'name': 'orbitnumber', 'content': '40987'},
        {'name': 'relativeorbitnumber', 'content': '92'}],
       'double': [{'name': 'illuminationazimuthangle',
         'content': '59.946173880146'},
        {'name': 'illuminationzenithangle', 'content': '24.640389146107'},
        {'name': 'vegetationpercentage', 'content': '0.129605'},
        {'name': 'notvegetatedpercentage', 'content': '0.619016'},
        {'name': 'waterpercentage', 'content': '0.0'},
        {'name': 'unclassifiedpercentage', 'content': '0.258393'},
        {'name': 'mediumprobacloudspercentage', 'content': '17.067103'},
        {'name': 'highprobacloudspercentage', 'content': '20.104083'},
        {'name': 'snowicepercentage', 'content': '0.0'},
        {'name': 'cloudcoverpercentage', 'content': '97.377396'}],
       'str': [{'name': 'level1cpdiidentifier',
         'content': 'S2A_OPER_MSI_L1C_TL_2APS_20230428T092502_A040987_T37NCC_N05.09'},
        {'name': 'gmlfootprint',
         'content': '<gml:Polygon srsName="http://www.opengis.net/gml/srs/epsg.xml#4326" xmlns:gml="http://www.opengis.net/gml">\n   <gml:outerBoundaryIs>\n      <gml:LinearRing>\n         <gml:coordinates>2.712828867980002,37.2009437938654 2.713900094942792,38.18851847180445 1.720620458966245,38.18905937759979 1.71994158954871,37.20214235599634 2.712828867980002,37.2009437938654</gml:coordinates>\n      </gml:LinearRing>\n   </gml:outerBoundaryIs>\n</gml:Polygon>'},
        {'name': 'footprint',
         'content': 'MULTIPOLYGON (((37.20214235599634 1.71994158954871, 38.18905937759979 1.720620458966245, 38.18851847180445 2.713900094942792, 37.2009437938654 2.712828867980002, 37.20214235599634 1.71994158954871)))'},
        {'name': 'format', 'content': 'SAFE'},
        {'name': 'processingbaseline', 'content': '05.09'},
        {'name': 'platformname', 'content': 'Sentinel-2'},
        {'name': 'filename',
         'content': 'S2A_MSIL2A_20230428T073611_N0509_R092_T37NCC_20230428T110612.SAFE'},
        {'name': 'instrumentname', 'content': 'Multi-Spectral Instrument'},
        {'name': 'instrumentshortname', 'content': 'MSI'},
        {'name': 'size', 'content': '1011.32 MB'},
        {'name': 's2datatakeid', 'content': 'GS2A_20230428T073611_040987_N05.09'},
        {'name': 'producttype', 'content': 'S2MSI2A'},
        {'name': 'platformidentifier', 'content': '2015-028A'},
        {'name': 'orbitdirection', 'content': 'DESCENDING'},
        {'name': 'platformserialidentifier', 'content': 'Sentinel-2A'},
        {'name': 'processinglevel', 'content': 'Level-2A'},
        {'name': 'datastripidentifier',
         'content': 'S2A_OPER_MSI_L2A_DS_2APS_20230428T110612_S20230428T075437_N05.09'},
        {'name': 'granuleidentifier',
         'content': 'S2A_OPER_MSI_L2A_TL_2APS_20230428T110612_A040987_T37NCC_N05.09'},
        {'name': 'identifier',
         'content': 'S2A_MSIL2A_20230428T073611_N0509_R092_T37NCC_20230428T110612'},
        {'name': 'uuid', 'content': 'f0223da2-d13f-40a2-b09a-e8d10a016ccb'}]}}}




```python
#searchResult
searchResult['feed']['entry']
#for name in searchResult['feed']['entry']:
#    print(name['title'])
```




    {'title': 'S2A_MSIL2A_20230428T073611_N0509_R092_T37NCC_20230428T110612',
     'link': [{'href': "https://scihub.copernicus.eu/dhus/odata/v1/Products('f0223da2-d13f-40a2-b09a-e8d10a016ccb')/$value"},
      {'rel': 'alternative',
       'href': "https://scihub.copernicus.eu/dhus/odata/v1/Products('f0223da2-d13f-40a2-b09a-e8d10a016ccb')/"},
      {'rel': 'icon',
       'href': "https://scihub.copernicus.eu/dhus/odata/v1/Products('f0223da2-d13f-40a2-b09a-e8d10a016ccb')/Products('Quicklook')/$value"}],
     'id': 'f0223da2-d13f-40a2-b09a-e8d10a016ccb',
     'summary': 'Date: 2023-04-28T07:36:11.024Z, Instrument: MSI, Satellite: Sentinel-2, Size: 1011.32 MB',
     'ondemand': 'false',
     'date': [{'name': 'generationdate', 'content': '2023-04-28T11:06:12Z'},
      {'name': 'beginposition', 'content': '2023-04-28T07:36:11.024Z'},
      {'name': 'endposition', 'content': '2023-04-28T07:36:11.024Z'},
      {'name': 'ingestiondate', 'content': '2023-04-28T13:06:47.279Z'}],
     'int': [{'name': 'orbitnumber', 'content': '40987'},
      {'name': 'relativeorbitnumber', 'content': '92'}],
     'double': [{'name': 'illuminationazimuthangle', 'content': '59.946173880146'},
      {'name': 'illuminationzenithangle', 'content': '24.640389146107'},
      {'name': 'vegetationpercentage', 'content': '0.129605'},
      {'name': 'notvegetatedpercentage', 'content': '0.619016'},
      {'name': 'waterpercentage', 'content': '0.0'},
      {'name': 'unclassifiedpercentage', 'content': '0.258393'},
      {'name': 'mediumprobacloudspercentage', 'content': '17.067103'},
      {'name': 'highprobacloudspercentage', 'content': '20.104083'},
      {'name': 'snowicepercentage', 'content': '0.0'},
      {'name': 'cloudcoverpercentage', 'content': '97.377396'}],
     'str': [{'name': 'level1cpdiidentifier',
       'content': 'S2A_OPER_MSI_L1C_TL_2APS_20230428T092502_A040987_T37NCC_N05.09'},
      {'name': 'gmlfootprint',
       'content': '<gml:Polygon srsName="http://www.opengis.net/gml/srs/epsg.xml#4326" xmlns:gml="http://www.opengis.net/gml">\n   <gml:outerBoundaryIs>\n      <gml:LinearRing>\n         <gml:coordinates>2.712828867980002,37.2009437938654 2.713900094942792,38.18851847180445 1.720620458966245,38.18905937759979 1.71994158954871,37.20214235599634 2.712828867980002,37.2009437938654</gml:coordinates>\n      </gml:LinearRing>\n   </gml:outerBoundaryIs>\n</gml:Polygon>'},
      {'name': 'footprint',
       'content': 'MULTIPOLYGON (((37.20214235599634 1.71994158954871, 38.18905937759979 1.720620458966245, 38.18851847180445 2.713900094942792, 37.2009437938654 2.712828867980002, 37.20214235599634 1.71994158954871)))'},
      {'name': 'format', 'content': 'SAFE'},
      {'name': 'processingbaseline', 'content': '05.09'},
      {'name': 'platformname', 'content': 'Sentinel-2'},
      {'name': 'filename',
       'content': 'S2A_MSIL2A_20230428T073611_N0509_R092_T37NCC_20230428T110612.SAFE'},
      {'name': 'instrumentname', 'content': 'Multi-Spectral Instrument'},
      {'name': 'instrumentshortname', 'content': 'MSI'},
      {'name': 'size', 'content': '1011.32 MB'},
      {'name': 's2datatakeid', 'content': 'GS2A_20230428T073611_040987_N05.09'},
      {'name': 'producttype', 'content': 'S2MSI2A'},
      {'name': 'platformidentifier', 'content': '2015-028A'},
      {'name': 'orbitdirection', 'content': 'DESCENDING'},
      {'name': 'platformserialidentifier', 'content': 'Sentinel-2A'},
      {'name': 'processinglevel', 'content': 'Level-2A'},
      {'name': 'datastripidentifier',
       'content': 'S2A_OPER_MSI_L2A_DS_2APS_20230428T110612_S20230428T075437_N05.09'},
      {'name': 'granuleidentifier',
       'content': 'S2A_OPER_MSI_L2A_TL_2APS_20230428T110612_A040987_T37NCC_N05.09'},
      {'name': 'identifier',
       'content': 'S2A_MSIL2A_20230428T073611_N0509_R092_T37NCC_20230428T110612'},
      {'name': 'uuid', 'content': 'f0223da2-d13f-40a2-b09a-e8d10a016ccb'}]}




```python
#fileName = searchResult['feed']['entry'][1]['title']
#downloadLink = searchResult['feed']['entry'][1]['link'][0]['href']
fileName = searchResult['feed']['entry']['title']
downloadLink = searchResult['feed']['entry']['link'][0]['href']
```


```python
file = requests.get(downloadLink,auth=('sebastiannormann', 'Goatscanfly_2022'))
```


```python
file
```




    <Response [200]>




```python
# save file
with open('satData/'+fileName+'.zip','wb') as f:
    f.write(file.content)
```


```python
# unzip file
from zipfile import ZipFile

with ZipFile("satData/"+fileName+".zip", 'r') as zObject:
    zObject.extractall(
      path="satData/")
```


```python

```
