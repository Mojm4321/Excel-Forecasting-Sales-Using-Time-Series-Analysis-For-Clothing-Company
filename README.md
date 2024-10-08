# Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company By Jolly Madamedon

## Introduction 
This report applies time series analysis to forecast monthly sales for a clothing company. The goal is to capture trends, identify seasonal patterns, and generate reliable sales forecasts using historical data. 

## Data Description
The dataset includes monthly sales data over 4 years with the following variables: Sales(Yt) - monthly sales figures, MA(12) – 12-month moving average used to smooth fluctuations and reveal long term trends, Seasonal Component(St) - seasonal factors affecting monthly sales, Deseasonalised Sales(Yt/St) - sales values adjusted for seasonality to isolate the trend, Forecast - predicted sales values based on trend and seasonal adjustments (see Diagram 1 & Diagram 2).

![Diagram 1](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/excel%20forecast%201.png)

Diagram 1


![Diagram 2](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/excel%20forecast%202.png)

Diagram 2

## Steps in Time Series Forecasting Process

### Plotting Time Series Data
Begin by visualising the data through the selection of a line chart with markers. Then designate the series name as 'Sales' and highlight the column containing the historical sales data. This will produce a line chart that illustrates the sales values, with markers representing each individual point (Diagram 3). 

To track both the year and month, the axis label range is selected to include both columns and data, to display the time periods on the chart's axes.

![Diagram 3](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/Line%20chart%20with%20markers%20Diagram%203.png)

Diagram 3

### Moving Average (MA) and Centered Moving Average(CMA)
To smooth the data, calculate a 12 month moving average by starting at the 7th cell and computing the average for the intial 12 months of data as shown in Diagram 4. This process should be repeated for each subsequent 12 month period up until the 4th year. However, the formula cannot be dragged down to the end of the dataset bas it would include data beyond the last 12 months of the period being analysed as illustrated in Diagram 5.

![Diagram 4](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/diagram%204%20excel.png)

Diagram 4

![Diagram 5](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/diagram%205%20excel.png)

Diagram 5

To calculate the centered moving average (CMA), average the surrounding MA values, centering the average around the current data point. In this case, '=AVERAGE(E9:E10)' is used, as shown in Diagram 6. Drag this formula down the column to apply it to all relevant cells, ensuring it does not extend beyond the last two MA values, as illustrated in Diagram 7. 

![Diagram 6](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/diagram%206%20excel%20forecasting.png)


Diagram 6

![Diagram 7](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/diagram%207%20excel%20forecasting.png)


Diagram 7

Once the CMA values have been calculated, they can be plotted alongside the Sales values to reveal the true direction of the sales trend. Overlaying the CMA on the Sales plot makes it easier to distinguish long term trends from seasonal variations and short term fluctuations (Diagram 8).

![Diagram 8](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/diagram%208%20excel%20forecasting.png)

Diagram 8

### Seasonal Component (St)
As the CMA removes irregularities and seasonality, the 'St/It' column is created to capture. To seasonality and irregularity components. To calculate this, divide the sales by the CMA. This formula is applied to all relevant cells, as shown in Diagram 9. For example: in cell G9, the value '0.96', indicates that in Year 1, month 7, the seasonality and irregularity components were 4% below the baseline, which in this case is represented by the CMA.

![Diagram 9](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/st%2Cit%20forecasting%20excel.png)

Diagram 9

### Quantifying Seasonal Components
Next, irregularities are removing and iseasonal components are isolated. This is done by averaging the St/It values for the same quarter across 4 years. For example, to calculate the seasonal component (St) for quarter 1 over four years, the formula =AVERAGE(G15,G27,G39) is used, which averages the values for year 2,3 and 4 because year 1 does not have an St/It value (see Diagram 10). 

Alternatively, a more efficient way is to use the AVERAGEIF function. This allows averaging based on the specific month across all years.For example: the formula =AVERAGEIF($C$9:$C$44,O19,$G$9:$G$44) selects the entire range of the 'Month' column, the cell containing the month being averaged, and the St/It range (see Diagram 11). This formula is applied to all months, and the results are then transferred into the main data column, as shown in Diagram 12.

![Diagram 10](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/diagram%2010%20excel%20forecasting.png)


Diagram 10


![Diagram 11](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/diagram%2011%20excel%20forecast.png)


Diagram 11


![Diagram 12](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/Diagram%2012%20forecast%20excel.png)


Diagram 12

### Deseasonalising Sales
Deseasonalising clothing sales data is achieved by dividing the actual sales figures by the seasonal component (St) for each time period. The formula is applied to the first row and then dragged down through the entire Yt/St column to adjust all sales values for seasonality. This is significant because it isolates the underlying trend in the data, illustrated in Diagram 13.

![Diagram 13](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/Diagram%2013%20forecast%20excel.png)

Diagram 13

### Trend Calculation Using Linear Regression 
The next step is to run a simple linear regression. Here the deseasonalised sales range will be the Y variable and the t will be the X variable, shown in Diagram 14. By fitting this regression, the coefficients of the intercept and slope are generated and used to create the calculate the trend component as illustrated in Diagram 15.

![Diagram 14](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/diagram%2014%20forecast%20excel%201.png)


Diagram 14


![Diagram 15](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/diagram%2015%20forecast%20excel.png)


Diagram 15

The formula to calculate the trend component will be =254.734368511233(coeff for intercept)+1.2363037537931(coeff for slope)*(t).The formula is applied to the first row and then dragged down through the entire Tt column as displayed in Diagram 16.

![Diagram 16](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/Diagram%2016%20excel%20forecasting.png)

Diagram 16

### Forecasting Future Sales
With the key components now generated, forecasting can be completed based on historical data for the avaliable time period. Forecasted sales are calculated by multiplying the Seasonal component (St) with the Trend component (Tt) (as shown in Diagram 17). This allowing for a comparison of the forecasted values with the actual sales data to evaluate the accuracy and strength of the model (see Diagram 18).


![Diagram 17](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/Diagram%2017%20forecast%20excel.png)


Diagram 17


![Diagram 18](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/Diagram%2018%20forecast%20excel.png)


Diagram 18

### Forecasting For Year 5
To predict future clothing sales for the next year, the time period is extended along with the months. The seasonal component column (St) automatically updates using the AVERAGEIF function, and the trend component column can be extended by applying the formula '=254.734368511233(coeff for intercept)+1.2363037537931(coeff for slope)*(t)'. With these two columns columns complete, the forecast for Year 5 can be completed. The forecasted sales are calculated by multiplying the year 5 St values by the corresponding Tt values, as illustrated in Diagram 19.


![Diagram 19](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/Diagram%2019%20forecast%20excel.png)


Diagram 19


Diagram 20 shows a comparison between the actual sales, the forecasted sales, and the 12 month centered moving average (CMA). 

![Diagram 20](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/Diagram%2020%20forecast%20excel.png)


Diagram 20


## Analysis of the Forecast

### Accuracy of Forecast vs Actual Sales
In the initial years, the forecasted sales track close to the actual sales, indicating that the model successfully captures the general trend and seasonal fluctuations in sales data. However, in Year 4, a slight divergence begins, especially in the latter months, where the forecast appears to understimate the sales, while the actual sales experience a noticeable dip and subsequent rise. This suggest that the model may struggle with capturing sudden shifts in sales patterns.

### Variability in Sales
There are sharp rises and falls evident in certain months. For instance, sales see an upward spike in October of Year 3, which could be attributed to a seasonal demand such as holiday shopping. October also marks the beginning of the winter shopping season, where consumers start purchasing warmer clothing such as coats, jackets and boots. 

On the other hand, the noticeable dip in February of Year 4, might be linked to post-holiday slowdowns as consumers recover from heavy spending during the holiday season. Also, winter clothing is typically on clearance, and demand for new collections may not be popular, as many brands could be preparing for the launch of spring collections. 

## Suggestion For Improvement (Model)
The SARIMA model, which accounts for both trend and seasonal components more thoroughly, might be the better solution for forecasting the sales for the clothing company.

## Suggestion For Improvement (Company)
Given the seasonal spikes, the company could plan its inventory accordingly, stocking up before high demand periods and reducing inventory after. Also, capitalising on predictable seasonal trends, for example: offering discounts right before anticipated peaks to drive sales up even more.