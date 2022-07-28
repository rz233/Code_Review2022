# Dashboard for Sensor Data
This folder contains code for create a dashboard for the sensor data to monitor the violations and speed for each vehicle. The figures in the dashboard have two main components:

  1. figures for all of data
  
      (1) calculate the number of total violations(medium violation + extreme violation) 
    per week and the number of extreme violations per week for each vehicle
  
  2. firgues for past two weeks
  
     (1) the number of violation for each violation type for each vehicle
     
     (2) the number of total violations(medium violation + extreme violation) per day and the number of extreme violations per day for each vehicle 
     
     (3) the number of violations per 100km for all vehicles
     
     (4) the number of violations per 100km for all vehicles(without outlier in distance)
     
     (5) 85th pert of speed each day each hr for each vehicle within same route
     
     (6) a summary table including the number of violation type; first & last online date in sensor data and first & last online date in eco data; and numbe of online days in past two weeks
     
 ## Data
 The following sensor data are originally from two different datasets: sensor data and eco data. Sensor data mainly have timestamp and speed informarion for each vechile.Eco data mainly have timestamp and different types fo violation information. 
  By combining these two datasets, we have the following two sensor data. 
 * sensor_day.gz.parquet
 
 different kinds of violations and different speed statistics at daily level
 
 * sensor_dayhr.gz.parquet
 
 different kinds of violations and different speed statistics at hourly level
 
## Requirements 

* Python3

* Pandas

* datetime

* Plotly

## Usage example

If we want to have a dashboard of past two weeks ending on 2022,6,21 (20220-6-08 to 2022-06-21)

```python
report = weekly_report(folder_path,outputs_path,2022,6,21)

report.return_all_figure_div()
```


Note: for now, need to change the title and final dashboard filename manually in the html session

```python
 html_string = '''
        <html>
            <head>
            <script src="https://cdn.plot.ly/plotly-latest.min.js"></script>
            </head>
            <body>
              <h1>Weekly Report: 6/08/2022 - 6/21/2022</h1>
              
            .....
              
            
            </body>
        </html>'''

        with open(self.outputs_path + "/" + "weekly_report_20220608-20220621.html", 'w') as f:
            f.write(html_string)
```
