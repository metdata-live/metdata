<p align="center">
<img src="https://hu.metdata.live/public/img/met_data.png" alt="metdata" width="400" height="400"/>
</>

# MetData
The MetData project focuses on to visualize synoptic and model meteorological data obtained from the Hungarian Meteorological Service.
The data is temporarily stored and synchronized for fast visualization and retrieval.


[:earth_africa: Project Website](https://hu.metdata.live ) 
## Dashboards
### Synoptic Dashboard
* Displays real-time synoptic meteorological data sourced from the Hungarian Meteorological Service.
* Data is uploaded in every 10 minutes, and it is synchronized with a 2 minutes time delay.
* [:bar_chart: dashboard ](https://hu.metdata.live/d/al_dUEa7k1/synop?orgId=1)
* [:floppy_disk: datasource](https://odp.met.hu/weather/weather_reports/synoptic/hungary/10_minutes/)

#### Used parameters

| Parameter | Description            |
|-----------|------------------------|
|    t      | Air temperature (2m)   |
|    v      | Horizontal Visibility  |
|    td     | Relative humidity (2m) |
|    p      | Station-level pressure |
|    fs     | Wind speed (10 m)      |
|    fx     | Wind Gust (10m)        |
|    r      | Precipitation (mm/h)   |

### Model Dashboard

* Presents predictive meteorological data obtained from models such as AROME and WRF.
* Allows comparison of different models run against each other and with synoptic weather data.
* Model runs are scheduled at specific UTC times: 00:00, 06:00, 12:00, and 18:00. The results are downloaded after the runs end.
  * The data sync charts provide information about the WRF/AROME model result sync status.
* [:bar_chart: dashboard link](https://hu.metdata.live/d/a970799a-514e-4ce6-a84a-de38970c907e/model?orgId=1)
* :floppy_disk: datasources:
  * [AROME](https://odp.met.hu/weather/nwp/AROME/nc/)
  * [WRF](https://odp.met.hu/weather/wrf/AROME/nc/)
* additional information
  * [AROME](https://odp.met.hu/weather/nwp/AROME/Description_shortrange_forecast-AROME-en.pdf)
  * [WRF](https://odp.met.hu/weather/nwp/WRF/Description_shortrange_forecast-WRF-en.pdf)

#### Used parameters

| Parameter       | Description                                       | AROME              | WRF                |
|-----------------|---------------------------------------------------|--------------------|--------------------|
| T2              | temperature at 2 meters                           | :white_check_mark: | :white_check_mark: |
| RelHum2         | relative humidity at 2 meters                     | :white_check_mark: | :heavy_minus_sign: |
| U10             | U-component of wind at 10 meters                  | :white_check_mark: | :white_check_mark: | 
| V10             | V-component of wind at 10 meters                  | :white_check_mark: | :white_check_mark: | 
| u_bpl           | eastward wind in the planetary boundary layer     | :white_check_mark: | :heavy_minus_sign: | 
| v_bpl           | northward wind in the planetary boundary layer    | :white_check_mark: | :heavy_minus_sign: | 
| T_bpl           | temperature in the planetary boundary layer       | :white_check_mark: | :heavy_minus_sign: | 
| RelHum_pbl	  | relative humidity in the planetary boundary layer | :white_check_mark: | :heavy_minus_sign: | 
---

### :floppy_disk: Datasources
<p align="center">
1. Hungarian Meteorological Service.
</>
<p align="center">
	 <img src="https://www.met.hu/images/logo/omsz_logo_374x135.png" alt="omsz" width="124.5" height="45"/>
</>


## How to help
Whenever you find an issue or have a suggestion, please file it here: https://github.com/metdata-live/metdata/issues

---
## System Components
### Grafana Dashboard
* Custom Grafana build, based on version: [10.1.5](https://github.com/grafana/grafana/releases/tag/v10.1.5)
* Hosts publicly accessible dashboards.

## Scheduled Jobs
* Specific jobs scheduled to download meteorological data from the National Meteorological Service periodically.

#### Synoptic Data Sync Job
* Retrieves synoptic data every 10 minutes.

#### Model Data Sync Job
* Schronizes AROME and WRF model runs.

### API Server
* Dedicated server acting as a Grafana data source.
* Optimized data communications between the Grafana client and the database.

