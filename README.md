# Project Overview

The Atlas Chain project contains the following major parts 
1. The map tiles - This can be of 2 types raster maps and vector maps. Raster maps are essentially images of the terrain that are taken at various zoom levels. Projects like OSM, Mapbox, etc have these maps available tiles available on the internet using a REST or similar scheme. For the purpose of proving the concept we would be leveraging these public map data, however the intent is to store this data on the blockchain so sensitive areas can also be made accessible in a safe manner.

2. The mapping software - The function of the mapping software is to handle the manipulation of the map. The software provides ways to add points, polygons, layers, etc on the map. It overlays the data on the map and gives extension points to format the data appropriately. There are two popular mapping software that we can look at - Leaflet.js (http://leafletjs.com/) and Google Maps API (https://developers.google.com/maps/). 
Leaflet is quite flexible when it comes to the underlying tiles and the data. The Google Maps API has the advantage of bringing it's own map tile data directly. 

3. The data - A map without data is not very interesting. And the data overlaid on the map is the key to Atlas chain. The popular data-structure used for javascript maps data seems to be GeoJSON http://geojson.org/. You can upload public datasets to https://carto.com/ and get that converted to GeoJSON datasets for use by the mapping software. The GeoJSON object would be the one that we store on the blockchain with permissions.

4. Data Access - The Atlas Chain aims to provide decentralised and on demand access to GIS based data in a manner that allows progressive enhancement of the information that is relevant to the user. The data access would be based on a list of tokens (claims) that the user's client can submit in order to get the required access. 
We will build this system as a semi-private blockchain with nodes in the various departments and organisations that want to participate. The data is stored encrypted in all the nodes in the form of versions with the map displaying the latest version by default. 

Design - 
In the PoC we shall leverage existing data and maps to the extent possible. The data would be in the form of an array of GeoJSON objects that would be progressively applied based on the claim exhibited by the user. We will use Google Maps API to load GeoJSON (https://developers.google.com/maps/documentation/javascript/datalayer). There will be a simple claim verification which would then allow adding additional GeoJSON layers. 

As we build out the initial version of the system we would provide mechanisms to index the data in the form of R-Trees(https://en.wikipedia.org/wiki/R-tree) to improve performance and reduce data bandwidth. 

The blockchain would contain multiple sources of information ranging from maps and GIS information to text, links and images that can be pulled in. The client would first communicate with a smart contract to get the claim tokens that would be used to obtain the information that they would need. The information would be retrieved automatically based on their location and context. 
