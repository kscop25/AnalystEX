# KScopis - RISI Data Analyst Candidate Exercise
## Overview
Following code sets working directory, reads data into R environment, cleans datasets, unzips files, and describes cookbook to create a map


## Deliverable:

	### code assumes the following packages are installed: cowplot, datasets, dplyr, ggplot2, ggrepel, ggspatial, grDevices, graphics, leaflet, libwgeom, methods, raster, sf, snakecase, spData, spDataLarge, stats, tmap, tmaptools, xlsx
	
library(base)
setwd("~/Desktop")  #set working directory

## Cleaning Datasets

	### uploaded Rural Atlas manually through GUI, read.csv command returned with unaddressed nulls/not all files are csv
	### read csv files into environment, proclaim headers TRUE - this will set column names to first row values

rural_atlas <- unzip("Rural_Atlas_Update23.zip")
people = read.csv("People.csv", header = T)
jobs = read.csv('Jobs.csv', header = T)
income = read.csv("Income.csv", header = T)
veterans = read.csv("Veterans.csv", header = T)
county_classifications = read.csv("County Classifications.csv", header = T)
variable_name_lookup = read.csv("Variable Name Lookup.csv", header = T)

	### for each dataset, take all non-integer columns and headers and convert to snakecase using snakecase package

library(snakecase)
as.character(people$state)
as.character(people$county)
people$state <- to_snake_case(people$state)
people$county <- to_snake_case(people$county)
names(people) <- to_snake_case(names(people))

![people](https://user-images.githubusercontent.com/89413212/131079491-ab93492a-5750-47b7-8bc4-72646d0fb5ad.png)

as.character(jobs$state)
as.character(jobs$county)
jobs$state <- to_snake_case(jobs$state)
jobs$county <- to_snake_case(jobs$county)
names(jobs) <- to_snake_case(names(jobs))

![jobs](https://user-images.githubusercontent.com/89413212/131079528-ec5bc1c7-6608-4778-bfb0-6c1eec28e786.png)

as.character(veterans$county)
as.character(veterans$state)
veterans$state <- to_snake_case(veterans$state)
veterans$county <- to_snake_case(veterans$county)
names(veterans) <- to_snake_case(names(veterans))

![veterans](https://user-images.githubusercontent.com/89413212/131079542-725816b4-9764-492e-81db-64f5339ca9e4.png)

as.character(county_classifications$county)
as.character(county_classifications$state)
county_classifications$state <- to_snake_case(county_classifications$state)
county_classifications$county <- to_snake_case(county_classifications$county)
names(county_classifications) <- to_snake_case(names(county_classifications))

![c_c](https://user-images.githubusercontent.com/89413212/131079609-6194b70d-da4f-477a-81c3-2c20cfd75b8f.png)

as.character(variable_name_lookup$Category)
as.character(variable_name_lookup$varShort)
as.character(variable_name_lookup$varLong)
names(variable_name_lookup) <- to_snake_case(names(variable_name_lookup))
variable_name_lookup$category <- to_snake_case(variable_name_lookup$category)
variable_name_lookup$var_short <- to_snake_case(variable_name_lookup$var_short)
variable_name_lookup$var_long <- to_snake_case(variable_name_lookup$var_long)
names(variable_name_lookup) <- to_snake_case(names(variable_name_lookup))

![vnl](https://user-images.githubusercontent.com/89413212/131079578-d744ea5e-055c-4c81-b145-9a720cb6b5b9.png)

as.character(income$State)
as.character(income$County)
names(income) <- to_snake_case(names(income))
income$state <- to_snake_case(income$state)
income$county <- to_snake_case(income$county)

![income](https://user-images.githubusercontent.com/89413212/131079635-b9a233ac-2e34-4e24-8703-9b5bf4a9610a.png)


## Mapping
	### Due to increased CPU usage, mapping commands were not able to be successfully executed (explained below in Shortcomings section).  Below, I have explained the steps and cookbook necessary to complete mapping section.
	### Mapping file types: .dbf, .prj, .shx, .cpg, .xml, .shp.  Variable file types: .csv, .txt
	
	Start by loading in shapefile (cb_2018_us_county_500k.shp) to create map boundaries 
	
	
	ggplot(data = cb_2018_us_county_500.shp) +
			geom_sf +
			geom_text(data = DATASET, aes(x=X, y+Y, label = "Economic conditions for New England, 2017"), 
					color = "grey22", fontface = "bold", check_overlap = FALSE) +
				annotate(geom = "text", x = -90, y =26, label = "New England",
				fontface = "italic", color "darkblue", size = 4) +
				coord_sf(xlim = c(xxx, xxx), ylim = c(xxx, xxx), expand = TRUE)
	
	
	### I would have liked to map the Income and Jobs datasets together, as well as the Veterans and Income.  
	

## Shortcomings
While the prompted delieverables were not intended to be complicated, the commands required to complete certain tasks - particularly the mapping portion - overburdened the RAM capabilities of my laptop, a 2011 4GB Macbook Air (see below).  

![summary](https://user-images.githubusercontent.com/89413212/131076609-78c40bee-8685-4f84-97c8-315bf877c20a.png)


This error appeared when attempting to plot border shapefile using ggplot2() + sf(), ending in a force quit of RStudio.

![error](https://user-images.githubusercontent.com/89413212/131076606-4b563e88-641a-4c84-aff8-fbcfbabd014f.png)

The CPU usage at times became so great it became impossible to view datasets.

![load](https://user-images.githubusercontent.com/89413212/131076870-c5af7f3d-d217-41dd-8f19-9ff2bb290b7a.png)

