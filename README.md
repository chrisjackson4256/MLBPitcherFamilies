# PitcherFamilies

Uses K-means clustering to categorize Major League Pitchers based on the physical characteristics of their fastball, breaking and offspeed pitches as well as data on pitch outcomes such as groundball/flyball perctanges, walks-to-strikeouts ratio, whiff rates and more.

### The Data

We scrape pitch-by-pitch data from Baseball Savant for the 2018 season using the pybaseball python package.  For each pitcher, we group their pitches into three categories: fastball, breaking pitch and offspeed pitch.  Then, for each pitch type, we compute the average speed, movement, spin rate and location.  We also compute the "arm slot angle" for each pitch type using the data on release location.

The information extracted from pitch-by-pitch data is then combined with the pitcher's seasonal data on pitch outcomes (e.g., ground ball rates, strike percentages, etc.).  The final dataset has 36 dimensions.

### The Clustering

Before performing the clustering, we split the dataset into two datasets based on the handedness of the pitcher.  Then, for each dataset, we perform Principal Component Analysis (PCA) in an attempt to reduce the dimenisonality of the data.  We require the reduced dataset still be able to explain 98% of the variance in the data.

To group the pitchers, we perform K-Means clustering and use the "Gap statistic" to find the optimal number of clusters.  For example, for left-handers, we find the optimal number of clusters is eight.   The clustering is shown below (projected down to two dimensions for visualization purposes only):

![alt text](https://github.com/chrisjackson4256/MLBPitcherFamilies/blob/master/lh_pitcher_cluster.png "lh pitcher clusters")

