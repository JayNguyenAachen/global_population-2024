# Global_population_2024
## Introduce 
- Name of project: Analysis of Global Population Structure and Aging Trends 2024.
- Objectives:
     - Classify countries based on age structure
     -  explore the relationship between demographic indicators (sex ratio, density, working age).
## Dataset
- <a href="https://github.com/JayNguyenAachen/global_population-2024/blob/main/global_population_stats_2024.csv">Dataset</a>
## Questions
- How is the child population (aged 0 to 14) distributed across countries? Do most countries have a low, medium, or high concentration of youth?
- How is the elderly population (aged 60 and over) distributed globally? Does this show a clear divide between developing and developed countries?
- How are the young (0-14 years old) and old (60+ years old) populations related? Does an inverse relationship exist (the younger the country, the less old it is) globally?
- What is the relationship between total population (Population(in millions)) and population density (Population density) of countries? Are the most populous countries (e.g. China, India) necessarily the most densely populated?
- How is the sex ratio (number of males per 100 females) distributed across countries? Do most countries have a balanced sex ratio (close to 100), and which sex are the largest differences (outliers)?
## Date interaction
<a href="https://github.com/JayNguyenAachen/global_population-2024/blob/main/Screenshot%202025-10-17%20190736.png">View Dashboard</a>

In power BI, users can use filter to select the country, the result demonstrates:<br>
     -'Country flag' <br>
     -'The number of population' <br>
     -'Male and Female ratio' <br>
     -'Independency ratio': The higher of number, the smaller the economic and social burden on the country's working-age population.
## Python process
#Check if there are null value 
```
print(text_file.isnull().sum())
```
#Determine what type of value 
```
print(text_file.dtypes)
```
#Descriptive Statistics
```
import seaborn as sns
import matplotlib.pyplot as plt
sns.histplot(data=text_file, x='Population Aged 0 to 14 (%)',kde=True, color="Blue" )
plt.title("Frequency of Population Aged 0 to 14 (%)")
plt.show()
```
<a href="https://github.com/JayNguyenAachen/global_population-2024/blob/main/unvariate0_14.png">Result</a>

```
sns.histplot(data=text_file, x='Population Aged 60 and Over (%)',kde=True, color="Blue" )
plt.title("Frequency of Population Aged 60 and Over (%)")
plt.show()
```
<a href="https://github.com/JayNguyenAachen/global_population-2024/blob/main/univariate_60.png">Result</a>

```
x = text_file['Population Aged 0 to 14 (%)']
y = text_file['Population Aged 60 and Over (%)']
plt.scatter(x,y)
plt.xlabel('Population Aged 0 to 14 (%)')
plt.ylabel('Population Aged 60 and Over (%)')
plt.show()
```
<a href="https://github.com/JayNguyenAachen/global_population-2024/blob/main/Scatterplot2.png">Result</a>

```
x = text_file['Population(in millions)']
y = text_file['Population density']
plt.scatter(x,y)
plt.xlabel('Population(in millions)')
plt.ylabel('Population density')
plt.show
```
<a href="https://github.com/JayNguyenAachen/global_population-2024/blob/main/ScatterPlot.png">Result</a>

```
sns.boxplot(x='Sex ratio (males per 100 females)' , data = text_file)
plt.title('Box Plot of Global Sex Ratio')
plt.show
```
<a href="https://github.com/JayNguyenAachen/global_population-2024/blob/main/BoxPlot.png">Result</a>

## Key findings
### 1. Extreme Polarization of Global Population Scale
The distribution of the total Population (in millions) is highly unequal and severely right-skewed (meaning it has a long tail of high values).

<strong>Evidence</strong>: <br>
The Median population is only around 9.46 million, which is vastly lower than the Mean (42.27 million).

<strong>Insight</strong>: <br>
This disparity confirms that the majority of countries are small-to-medium in population size. The mean is heavily distorted by a handful of extreme outliers (China, India, etc.) which dominate the global total, creating a highly centralized distribution.

<strong>Density Relationship</strong>: <br>
High population density is generally not correlated with high total population, as the highest density figures are found in smaller city-states and regions.

### 2. Strong Inverse Correlation in Age Structure
There is a powerful, clear negative correlation between the young population and the elderly population across countries.

<strong>Evidence</strong>: <br>
<strong>The Scatter Plot</strong> of Population Aged 0 to 14 (%) (Young) vs Population Aged 60 and Over (%) (Elderly) shows a distinct diagonal line from the bottom-right to the top-left. <br>

<strong>Insight</strong>: This demonstrates a definitive global demographic split: <br>

- **"Young" Nations:**
    - High youth percentage (Population Aged 0 to 14%).
    - Low elderly percentage (Population Aged 60 and Over %).
    - *Common in developing regions.*
- **"Aged" Nations:**
    - Low youth percentage.
    - High elderly percentage.
    - *Common in developed regions.*

<strong>Distribution Confirmation</strong>: <br>
The Histogram for the 60+ Age Group reinforces this by showing a clustering of countries at both the low end (Young) and a significant peak/tail at the high end (Aged).

### 3. Sex Ratio is Balanced, but Male Outliers Exist
The overall global distribution of the Sex ratio (males per 100 females) is generally close to balance, but outliers are a major factor.

<strong>Evidence</strong>: <br>
The Box Plot shows the Median is very close to $100$ (around $98.7$). This means $50\%$ of countries have a near-equal number of males and females.

<strong>Insight</strong>: <br>
The majority of the world is balanced. However, the plot reveals several extreme outliers (dots extending far to the right, up to $248$ males per $100$ females). These significant deviations are typically found in countries with high rates of male labor migration, leading to a heavily skewed ratio in those specific nations.


