# exploring-data-visualization
This repository contains three Jupyter notebooks containing case studies I used to learn about data visualization, using Matplotlib and Folium to perform the plotting. All three case studies use Kaggle's World Development Indicators dataset.

## World Development Indicator Database
<table>
<col width="550">
<col width="450">
<tr>
<td><img src="https://upload.wikimedia.org/wikipedia/commons/4/46/North_South_divide.svg" align="middle" style="width:550px;height:360px;"/></td>
<td>
In the notebooks, I will be using an open dataset from <a href="https://www.kaggle.com">Kaggle</a>. It is  <a href="https://www.kaggle.com/worldbank/world-development-indicators">The World Development Indicators</a> dataset obtained from the World Bank containing over a thousand annual indicators of economic development from hundreds of countries around the world.
<br>
<br>
This is a slightly modified version of the original dataset from <a href="http://data.worldbank.org/data-catalog/world-development-indicators">The World Bank</a>
<br>
<br>
List of the <a href="https://www.kaggle.com/benhamner/d/worldbank/world-development-indicators/indicators-in-data">available indicators</a> and a <a href="https://www.kaggle.com/benhamner/d/worldbank/world-development-indicators/countries-in-the-wdi-data">list of the available countries</a>.
</td>
</tr>
</table>


# 05a Matplotlib Notebook
## Step 1: Initial exploration of the Dataset
I begin by checking the shape of the database and saw that it is a really large dataset, at least in terms of the number of rows.  But with 6 columns, what does this hold?

After checking the shape of the database, I found that it is a four dimensional database that has different indicators for different countries with the year and value of the indicator. I then asked: 
1. How many UNIQUE country names are there ? - `countries = data['CountryName'].unique().tolist()
len(countries)`
2. Are there same number of country codes ?
3. Are there many indicators or few ?
4. How many years of data do we have ?
5. What's the range of years?

## Step 2: Matplotlib: Basic Plotting, Part 1
I picked a country and an indicator to explore: **CO2 Emissions per capita and the USA**
* Created a new dataframe: `stage` which shows those indicators matching the USA for country code and CO2 emissions over time
* Plotted a **bar graph** to see *how emissions have changed over time* using MatplotLib
  * *Findings:* The bar graph showed emissions per capita have dropped a bit over time 
* Plotted a **line graph** to make the graphic a bit more appealing before I continuing to explore it 
* Plotted a **Histogram** to explore the distribution of values
  * This data as a histogram is better to explore the ranges of values in CO2 production per year
  * *Findings:* Found that the the USA has many years where it produced between 19-20 metric tons per capita with outliers on either side.
* Explored **how do the USA's numbers relate to those of other countries?** by plotting a histogram of the emmissions per capita by country
  *  *Findings:* found that he USA, at ~18 CO2 emissions (metric tons per capital) is quite high among all countries.

## Step 3: Matplotlib: Basic Plotting, Part 2
I then explored the *relationship between GPD and CO2 Emissions in USA* 
* Created a new dataframe: `gdp_stage` which shows those those indicators matching the USA for country code and CO2 emissions over time.
* Plotted using a **Line graph** GDP Per Capita in the USA 
  * *Findings:* Although we've seen a decline in the CO2 emissions per capita, it does not seem to translate to a decline in GDP per capita. For the most part, we're seeing solid growth, over time. There are a couple dips here and thereand one, noticeable dip in the recession around 2008. But the upper trend, is restored by 2010. So, knowing that CO2 emissions over that same time period didn't behave the same way, leads me to think that they aren't closely related. 


## Step 4: ScatterPlot for comparing GDP against CO2 emissions (per capita)
To make a scatterplot I needed to make sure I was looking at the same time frames. The reason we want make sure these are the same, is because scatter plots require the same number of years in the data set. 
* After Plotting the **scatter plot**, I used the correlation coefficient function in numpy to get back the relationship between these two arrays. The main diagonal is each against itself. So we expect to see 1.0 there or perfect correlation. But on the other diagonal, 0.077.

A correlation of 0.07 is pretty weak.



