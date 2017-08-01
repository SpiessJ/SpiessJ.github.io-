---
output: html_document---
The example at hand shows how quickly and neatly maps can be created with *Leaflet* in R.
```{r load package, echo = TRUE, eval=TRUE}library(leaflet) ## loading the package```
I created a file that contains longitudes, latitudes and popup text for some of the major cities I have visited.
```{r load and transform data, echo = TRUE, eval=TRUE}# load the file and convert to numericcitiestravel <-read.table("C:/users/johan/Documents/travel.txt", header = TRUE)citiestravel$long <- as.numeric(paste(citiestravel$long)) citiestravel$lat <- as.numeric(paste(citiestravel$lat)) 
# check the file before mappingstr(citiestravel)head(citiestravel)```
We finally draw the map. I decided not to use the label as I found it "overdone" (maps show the names of places). People should get curious and zoom in :-)
```{r lapply leaflet, echo = TRUE, eval=TRUE}leaflet(data = citiestravel) %>% addTiles() %>%                          addCircleMarkers(citiestravel$long, citiestravel$lat, popup = ~as.character(citiestravel$label), color = "#e6550d")```

