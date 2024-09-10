# Forecasting-Sales-Using-Time-Series-Analysis-For-Clothing-Company

## Introduction 
This report uses time series analysis to forecast monthly sales for a clothing company. The data was created to capture trends, identify seasonal patterns, and generate reliable sales forecasts. Techniques such as moving averages, seasonal decomposition and deseasonalising the sales were applied to make accurate projections.

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


