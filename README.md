### Estimation of high-resolution solar irradiance data using optimized semi-empirical satellite method and GOES-16 imagery

This repository includes the data as well as example scripts for data processing and figure production for the research paper: https://www.sciencedirect.com/science/article/pii/S0038092X22004236.

The following figure shows the flowchart for GHI estimation using semi-emipirical satellite method with several clear-sky models.

![image](https://user-images.githubusercontent.com/54800388/187680737-70c8ddb3-ab49-487a-acc1-d84fc631fba0.png)


#### Data
The satellite data of GOES-16 is downloaded via public available source, e.g., Amazon Web Services, for GOES-16, please refer to: https://docs.opendata.aws/noaa-goes16/cics-readme.html#accessing-goes-data-on-aws.

The used ground data is from SURFRAD stations (see the following table) with quality control.
The snow-free period is obtained using the data from National Aeronautics and Space Administration (NASA) National Snow and Ice Data Center (NSIDC): https://nsidc.org/data/nsidc-0719/versions/1.  
|Station|Latitude (°)|Longitude (°)|Altitude (m)|Timezone|Snow-free period|
|:-----:|:---------: | :---------: | :--------: |:------:| :------------: |
|  BON  |  40.05     | -88.37      |  230       |  UTC-6 | 2019-04-01 - 2019-10-31 |
|  DRA  |  36.62     | -116.02     |  1007      |  UTC-8 | 2019-01-01 - 2019-12-31 |
|  FPK  |  48.31     | -105.10     |  634       |  UTC-7 | 2019-05-03 - 2019-09-30 |
|  GWN  |  34.25     | -89.87      |  98        |  UTC-6 | 2019-01-01 - 2019-12-31 |
|  PSU  |  40.72     | -77.93      |  376       |  UTC-5 | 2019-04-01 - 2019-10-31 |
|  SXF  |  43.73     | -96.92      |  473       |  UTC-6 | 2019-05-01 - 2019-09-30 |
|  TBL  |  40.12     | -105.24     |  1689      |  UTC-7 | 2019-05-02 - 2019-09-30 |

#### Strategies for dynamic range, upper and lower bounds determination

|Strategy|Time window*|Upper bound|Lower bound |
|:-----:|:---------: | :---------: | :--------:|
|  1  |  90 days (moving) | mean of 20 highest values|mean of 40 lowest values| 
|  2  |  60 days (moving) | mean of 20 highest values|mean of 40 lowest values|
|  3  |  30 days (moving) | mean of 10 highest values|mean of second to fifth lowest values|
|  4  |  1 month (fixed)  | mean of 10 highest values|mean of second to fifth lowest values| 

* Time window is used to determine the dynamic range, a moving time window means it moves with the time of interest,
so the upper and lower bound will change. While the monthly fixed time window means it is fixed in the month of
interest, so the upper and lower bounds remain constant in the month.

For an example using the four strategies for three bands, please refer to 

#### Clear-sky models
Four clear-sky models are used in this study.
