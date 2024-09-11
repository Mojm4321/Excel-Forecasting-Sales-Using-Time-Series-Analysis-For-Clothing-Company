# Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company By Jolly Madamedon

## Introduction 
This report uses time series analysis to forecast monthly sales for a clothing company. The data was created to capture trends, identify seasonal patterns, and generate reliable sales forecasts. 

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

Now the CMA values have been calculated, they can be plotted alongside the Sales values to reveal the true direction of the sales trend. Overlaying the CMA on the Sales plot makes it easier to distinguish long term trends from seasonal variations and short term fluctuations (Diagram 8).

![Diagram 8](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/diagram%208%20excel%20forecasting.png)

Diagram 8

As mentioned, the Centered Moving Average (CMA) removes irregularities and seasonality, leading to the creation of the 'St/It' column. To calculate the seasonality/irregularity components, divide the sales by the CMA using the formula. This formula is then applied to all relevant cells, as shown in Diagram 9. For example: in cell G9, the value '0.96', indicates that in Year 1, month 7, the seasonality and irregularity components were 4% below the baseline, which in this case is represented by the CMA.

![Diagram 9](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/st%2Cit%20forecasting%20excel.png)

Diagram 9

The next step involves removing irregularities and isolating the seasonal components to quantify them. This is done by averaging the St/It values for the same quarter across 4 years. For example, to calculate the seasonal component (St) for quarter 1 over four years, the formula =AVERAGE(G15,G27,G39) is used, which averages the values for year 2,3 and 4 because year 1 does not have an St/It value (see Diagram 10). 

Alternatively, a more efficient way is to use the AVERAGEIF function. This allows averaging based on the specific month across all years.For example: the formula =AVERAGEIF($C$9:$C$44,O19,$G$9:$G$44) selects the entire range of the 'Month' column, the cell containing the month being averaged, and the St/It range (see Diagram 11). This formula is applied to all months, and the results are then transferred into the main data column, as shown in Diagram 12.

![Diagram 10](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/diagram%2010%20excel%20forecasting.png)


Diagram 10


![Diagram 11](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/diagram%2011%20excel%20forecast.png)


Diagram 11


![Diagram 12](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/Diagram%2012%20forecast%20excel.png)


Diagram 12

Now the focus is on deseasonalising the data. This is acheived by dividing the actual sales figures by the seasonal component (St) for each corresponding tiime period. The formula is applied to the first row and then dragged down through the entire Yt/St column to adjust all sales values for seasonality. This is significant because it isolates the underlying trend in the data, illustrated in Diagram 13.

![Diagram 13](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/Diagram%2013%20forecast%20excel.png)

Diagram 13

The next step is to run a simple linear regression. Here the deseasonalised sales range will be the Y variable and the t will be the X variable, shown in Diagram 14. By fitting this regression, the coefficients of the intercept and slope are generated and used to create the calculate the trend component as illustrated in Diagram 15.

![Diagram 14](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/diagram%2014%20forecast%20excel%201.png)


Diagram 14


![Diagram 15](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/diagram%2015%20forecast%20excel.png)


Diagram 15

The formula to calculate the trend component will be =254.734368511233(coeff for intercept)+1.2363037537931(coeff for slope)*(t).The formula is applied to the first row and then dragged down through the entire Tt column as displayed in Diagram 16.

![Diagram 16](https://github.com/Mojm4321/Excel-Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company/blob/main/Diagram%2016%20excel%20forecasting.png)

Diagram 16



