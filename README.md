# Examination of the North Atlantic ciculation
_This project is a segment of the [Global change - a data-driven approach](https://www.hc.rwth-aachen.de/cms/HC/Events/HCSS/HCSS2021/~ntcpe/GlobalChange/lidx/1/) course, offered at the [RWTH Aachen University Honors College Summer School 2021](https://www.hc.rwth-aachen.de/cms/hc/events/hcss/~ursik/hcss2021/?lidx=1)._

Contributors:
 - Leonie Gellweiler
 - [Til Mohr](https://github.com/CodingTil/)
 - Sven Neubauer

## Impact of the North Atlantic circulation on the climate in Europe
![North Atlantic circulation](./images/gulf_stream_visu.png)

The North Atlantic circulation, particularly the Gulf Stream, plays a critical role in shaping Western and Central Europe's climate. This system transports warm water from the Gulf of Mexico to the North Atlantic, influencing the air temperature above it and subsequently affecting Europe's weather through westerly winds. When this water reaches near Iceland, it cools and sinks, flowing back towards the Gulf of Mexico.

With ongoing climate change, there's a concern that this circulation might weaken, potentially leading to a paradoxical cooling effect in Europe amidst global warming. This could be influenced by factors like the melting of the Greenland ice sheet, which introduces fresh water into the North Atlantic, disrupting the water's density and circulation strength.

## Project goal
Our project aims to investigate the North Atlantic circulation's current state and its influence on Europe's climate. Utilizing datasets from [Google Earth Engine](https://earthengine.google.com/), we'll examine if there's evidence of the North Atlantic circulation weakening. Our focus areas are the warming Gulf of Mexico and the cooling North Atlantic, indicated as the red (warm) and blue (cold) regions in our study.

![Regions of interest](./images/regions_of_interest.png)

## Data Utilized
![HYCOM](./images/datasets.png)

We have decided to use the following datasets for our analysis:
 - HYCOM: Hybrid Coordinate Ocean Model, Water Temperature and Salinity
 - HYCOM: Hybrid Coordinate Ocean Model, Water Velocity

### Dataset Properties
| Property | Description |
| --- | --- |
| Spatial resolution | $1/12°$ |
| Temporal resolution | 1992-10-02 to present<br>$3h$ spacing |
| Bands | Temperature ($C$)<br>Salinity ($psu$)<br>Velocity_x ($m/s$)<br>Velocity_y ($m/s$) |
| Depths | $0m - 500m$ across $40$ levels |

### Data Extraction
Our dataset initially encompassed over $10600$ days of images, $8$ images per day, and $4 \cdot 40$ bands per image. To manage this vast data, we:
 - Reduced temporal resolution to weekly averages, yielding $1500$ images
 - Applied spatial resolution reduction techniques, calculating statistical measures like minimum, maximum, mean, median, variance, and skewness for each area of interest

This approach significantly compressed the data, leaving us with about 1000 weekly values per region, totaling around 23MB of data per area.

## Analysis
### Temperature
![Temperature Warm](./images/temperature_warm.png)
![Temperature Cold](./images/temperature_cold.png)

Surface temperatures reflect seasonal changes more prominently, while deeper levels maintain steadier temperatures. Notably, the Gulf Stream ensures the warm region remains warmer than the cold region. Over the decades, the warm region's temperatures have risen, whereas the cold region exhibits a slight cooling trend.

### Salinity
![Salinity Warm](./images/salinity_warm.png)
![Salinity Cold](./images/salinity_cold.png)

Salinity trends are more pronounced, with the warm region experiencing increased salinity in both shallow and deep waters. Conversely, the cold region's salinity decreases, possibly due to fresh water influx from melting ice. These trends suggest a weakening in the North Atlantic circulation.

### Velocity
Our velocity data analysis showed significant instability, particularly in shallow waters. Therefore, we focused on deeper water velocities, measuring them as the euclidean norm of the x- and y-direction velocities.

![Velocity Warm](./images/velocity_warm.png)
![Velocity Cold](./images/velocity_cold.png)

The velocity data indicated a slight reduction in water movement in the warm region and a marginal increase in the cold region. However, the minimal scale of these changes (in $m/s$) makes this data less definitive than temperature and salinity findings.

### Correlation between temperature and salinity across multiple depths
![Correlation Warm](./images/correlation_warm.png)
![Correlation Cold](./images/correlation_cold.png)

A noteworthy observation is the varying correlation between temperature and salinity at different depths. In both regions, these factors show an inverse correlation in shallower waters, a direct correlation around $600m$ depth, and no significant correlation beyond $1200m$ depth. The reasons for these patterns remain a subject for further research.

## Conclusion
Our findings indicate a decrease in temperature and salinity in the North Atlantic's colder region, contrasting with increases in the warmer Gulf of Mexico region. These trends align with the hypothesis of a weakening North Atlantic circulation.

## Further Reading and References
 - [Caesar, Levke, Stefan Rahmstorf, Alexander Robinson, Georg Feulner, and V. Saba. "Observed fingerprint of a weakening Atlantic Ocean overturning circulation." Nature 556, no. 7700 (2018): 191-196](https://www.nature.com/articles/s41586-018-0006-5)
 - [Chen, Xianyao, and Ka-Kit Tung. "Global surface warming enhanced by weak Atlantic overturning circulation." Nature 559, no. 7714 (2018): 387-391.](https://www.nature.com/articles/s41586-018-0320-y)
