The National Earthquake Information Center (NEIC) determines the location and size of all significant earthquakes that occur worldwide and disseminates this information immediately to national and international agencies, scientists, critical facilities, and the general public. The NEIC compiles and provides to scientists and to the public an extensive seismic database that serves as a foundation for scientific research through the operation of modern digital national and global seismograph networks and cooperative international agreements.
GG501 - Assignment 1
Xue Qing Chen
2024-Feb-16
R Markdown
This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents. For more details on using R Markdown see http://rmarkdown.rstudio.com.

When you click the Knit button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:

summary(cars)
##      speed           dist       
##  Min.   : 4.0   Min.   :  2.00  
##  1st Qu.:12.0   1st Qu.: 26.00  
##  Median :15.0   Median : 36.00  
##  Mean   :15.4   Mean   : 42.98  
##  3rd Qu.:19.0   3rd Qu.: 56.00  
##  Max.   :25.0   Max.   :120.00
Including Plots
You can also embed plots, for example:



Note that the echo = FALSE parameter was added to the code chunk to prevent printing of the R code that generated the plot.

Assignment 1 - Exploratory Visualization in ggplot2 and data storytelling
Instructions: This is an individual assignment, submit the answer to the following as a hard-copy in class by Feb 16th.

[2 marks] Explain in a couple of sentences why you selected this dataset.
My answer is written here and is going to clearly articulate what dataset I selected and why I selected this dataset for my analysis.

#code to read in data into a tibble
#***********************************
library(readr)
## Warning: package 'readr' was built under R version 4.3.2
df <- read_csv("https://vincentarelbundock.github.io/Rdatasets/csv/openintro/snowfall.csv", 
            col_types = list( 
            year_start = col_integer(), 
            year_end = col_integer(), 
            total_snow = col_double())
              )
The reason to select the “snowfall” dataset from the OpenIntro repository is because it offers a comprehensive collection of historical snowfall data from various regions over multiple years. This dataset aligns with the interest in exploring trends and patterns in snowfall accumulation, enabling analysis of variations in snowfall amounts across different years and locations. Understanding past snowfall patterns is essential for climate research, urban planning, and recreational activities, making this dataset valuable for diverse applications.

[5 marks] Create a bar plot using ggplot2 graphing. Write a sentence interpreting what is happening in the graph. Make sure you read up on the documentation of the data to understand what is represented and how it was measured.
Answer: Write your code and answer here.

library(ggplot2)
## Warning: package 'ggplot2' was built under R version 4.3.2
library(readr)
df <- read_csv("https://vincentarelbundock.github.io/Rdatasets/csv/openintro/snowfall.csv", 
               col_types = list( 
                 year_start = col_integer(), 
                 year_end = col_integer(), 
                 total_snow = col_double())
)
ggplot(df, aes(x = factor(year_start), y = total_snow)) +
  geom_bar(stat = "identity", fill = "skyblue") +
  labs(title = "Total Snowfall by Year",
       x = "Year",
       y = "Total Snowfall (inches)") +
  theme_minimal() +
  scale_x_discrete(breaks = seq(min(df$year_start), max(df$year_start), by = 5))
## Warning: Removed 9 rows containing missing values (`position_stack()`).


The bar plot illustrates the total snowfall (in inches) for each year represented in the dataset. Each bar corresponds to a specific year, with the x-axis displaying years in intervals of 5 years. The plot provides a visual representation of the variation in snowfall across different years, indicating potential trends or patterns over time.

[5 marks] Create a line or point plot using ggplot2 graphing. Write a sentence interpreting what is happening in the graph. Make sure you read up on the documentation of the data to understand what is represented and how it was measured. Answer: Write your code and answer here:
library(ggplot2)
library(readr)
df <- read_csv("https://vincentarelbundock.github.io/Rdatasets/csv/openintro/snowfall.csv", 
               col_types = list( 
                 year_start = col_integer(), 
                 year_end = col_integer(), 
                 total_snow = col_double())
)
ggplot(df, aes(x = year_start, y = total_snow)) +
  geom_line(color = "blue") +
  geom_point(color = "blue") +
  labs(title = "Total Snowfall Over Time",
       x = "Year",
       y = "Total Snowfall (inches)") +
  theme_minimal()
## Warning: Removed 9 rows containing missing values (`geom_point()`).


The line plot shows the trend of total snowfall (in inches) over the years represented in the dataset. Each point on the line represents the total snowfall recorded for a specific year. The plot enables us to observe any overall increase, decrease, or fluctuations in snowfall over time, providing insights into long-term snowfall patterns.

[5 marks] Create any other plot of your choosing using ggplot2 graphing. Write a sentence interpreting what is happening in the graph. Make sure you read up on the documentation of the data to understand what is represented and how it was measured.
Answer: Write your code and answer here:

library(ggplot2)
library(readr)
df <- read_csv("https://vincentarelbundock.github.io/Rdatasets/csv/openintro/snowfall.csv", 
               col_types = list( 
                 year_start = col_integer(), 
                 year_end = col_integer(), 
                 total_snow = col_double())
)
ggplot(df, aes(x = year_start, y = total_snow)) +
  geom_point(color = "blue") +
  labs(title = "Relationship between Year and Total Snowfall",
       x = "Year",
       y = "Total Snowfall (inches)") +
  theme_minimal()
## Warning: Removed 9 rows containing missing values (`geom_point()`).


The scatter plot illustrates the relationship between the year and total snowfall (in inches) based on the data provided. Each point represents a specific year, with its corresponding total snowfall recorded during that year. The plot allows us to visually inspect any potential trends or patterns in snowfall over the years, providing insights into the variability of snowfall amounts across different years.

[15 marks] Select another dataset and tell a story with the data. Think about who a potential audience is for your story. Using the structure outlined in lecture slides, write a sentence or two for each phase of the data story: Opening, Challenge, Action, and Resolution. For each, include a visualization to illustrate (which may or may not be a graph of the data- external sources can be used here as well). In order to understand the context of the data, you will have to do some background research into the dataset this is generally available in the documentation. The story should include at least three graphs you create from the data(which must be labelled correctly and not be duplicates of graphs for questions 2-4).
Answer: Write your code and answer here:

Backgroud The iris dataset is one of the most famous datasets in the field of statistics and machine learning. It was introduced by the British statistician and biologist Ronald Fisher in his 1936 paper “The use of multiple measurements in taxonomic problems” as an example of linear discriminant analysis. The dataset consists of 150 samples of iris flowers, each belonging to one of three species: setosa, versicolor, and virginica. For each sample, four features were measured: the length and width of both the sepals and petals, in centimeters. Fisher collected and measured these samples from three different locations in the Gaspé Peninsula in Canada. The iris dataset has since become a benchmark for testing various classification algorithms due to its simplicity and clear delineation between classes, making it an excellent starting point for learning and teaching classification techniques.

Potential Audience The potential Audience is for data analysts or researchers, my focus shift towards statistical analysis and exploring patterns within the dataset using advanced techniques. For instance, applying clustering algorithms to identify distinct groups of iris species based on their characteristics, or using classification models to predict iris species based on given features. Providing access to interactive tools or coding notebooks where users can experiment with different analysis methods and visualize results could enhance their understanding and engagement with the dataset.

Opening: The iris dataset, a classic in the field of data analysis, offers valuable insights into the characteristics of different species of iris flowers. This dataset contains measurements of sepal and petal length and width for three species: setosa, versicolor, and virginica.

Challenge: One of the challenges in analyzing the iris dataset is understanding the variability and distribution of these measurements across different species. This involves exploring how the characteristics of each species compare and whether there are any distinct patterns or differences that can be identified.

Action: To address this challenge, we can utilize various visualizations to explore the data comprehensively. We will create a scatter plot to visualize the relationship between sepal length and width, a box plot to compare the distributions of petal lengths across species, and a histogram with a density line to illustrate the distribution of petal lengths within each species.

Resolution: Through our analysis, we discovered distinct clusters corresponding to each iris species based on their sepal and petal measurements. The scatter plot revealed clear separation between the species, with setosa exhibiting significantly different characteristics compared to versicolor and virginica. The box plot highlighted differences in petal length distributions, with setosa generally having shorter petals compared to versicolor and virginica. Finally, the histogram with a density line provided a detailed view of the distribution of petal lengths within each species, allowing for a deeper understanding of the variability and patterns present in the data. These visualizations offer valuable insights for botanists, researchers, and enthusiasts interested in understanding the characteristics and diversity of iris species.

Below are three visualizations illustrating different aspects of the Iris dataset:

1.Violin Plot of Sepal Width by Species: This violin plot illustrates the distribution of sepal width among different species.It offers insights into the range and distribution of sepal widths within each species, facilitating comparisons between them. 2.Histogram with density line ofor Petal Width: This histogram displays the distribution of petal widths across all iris species, providing insights into the overall variability of this measurement. 3.Box Plot of Sepal Length by Species: This box plot shows the distribution of sepal lengths for each iris species, highlighting any differences in the central tendency and variability.

Here are three visualizations created from the data:

library(ggplot2)
library(gridExtra)
## Warning: package 'gridExtra' was built under R version 4.3.2
violin_plot <- ggplot(data = iris, aes(x = Species, y = Sepal.Width, fill = Species)) +
  geom_violin(trim = FALSE) +
  labs(title = "Distribution of Sepal Width by Species (Violin Plot)",
       x = "Species",
       y = "Sepal Width",
       fill = "Species") +
  theme_minimal()
histogram_density <- ggplot(data = iris, aes(x = Petal.Length, fill = Species, color = Species)) +
  geom_histogram(aes(y=..density..), binwidth = 0.2, alpha = 0.6, position="identity") +
  geom_density(alpha = 0.5) +
  labs(title = "Histogram with Density Line for Petal Length",
       x = "Petal Length",
       y = "Density",
       fill = "Species",
       color = "Species") +
  theme_minimal()
box_plot <- ggplot(data = iris, aes(x = Species, y = Petal.Width, fill = Species)) +
  geom_boxplot() +
  labs(title = "Distribution of Petal Width by Species (Box Plot)",
       x = "Species",
       y = "Petal Width",
       fill = "Species") +
  theme_minimal()
grid.arrange(violin_plot, histogram_density, box_plot, nrow = 3)
## Warning: The dot-dot notation (`..density..`) was deprecated in ggplot2 3.4.0.
## ℹ Please use `after_stat(density)` instead.
## This warning is displayed once every 8 hours.
## Call `lifecycle::last_lifecycle_warnings()` to see where this warning was
## generated.


These three visualizations provide insights into different aspects of the iris dataset, such as the relationship between sepal length and width, the distribution of petal length by species, and the distribution of sepal width overall.

Visualization 1: Violin Plot of Sepal Width by Species:

library(ggplot2)
violin_plot <- ggplot(data = iris, aes(x = Species, y = Sepal.Width, fill = Species)) +
  geom_violin(trim = FALSE) +
  labs(title = "Distribution of Sepal Width by Species (Violin Plot)",
       x = "Species",
       y = "Sepal Width",
       fill = "Species") +
  theme_minimal()
print(violin_plot)


This violin plot visualizes the distribution of sepal width among different species of iris flowers. Each violin represents a species (setosa, versicolor, and virginica), and the width of the violin corresponds to the density of observations at different values of sepal width. It provides insights into the range and distribution of sepal widths within each species, allowing for comparison between them.

Visualization 2: Histogram with Density Line for Petal Length:

library(ggplot2)
histogram_density <- ggplot(data = iris, aes(x = Petal.Length, fill = Species, color = Species)) +
  geom_histogram(aes(y=..density..), binwidth = 0.2, alpha = 0.6, position="identity") +
  geom_density(alpha = 0.5) +
  labs(title = "Histogram with Density Line for Petal Length",
       x = "Petal Length",
       y = "Density",
       fill = "Species",
       color = "Species") +
  theme_minimal()
print(histogram_density)


The Histogram with Density Line for Petal Length visualizes the distribution of petal lengths across different species of iris flowers. This visualization allows us to understand the central tendency and spread of petal lengths within each species, as well as the overall distribution across all species. By examining the histogram bars and the overlaid density line, we can observe how petal length frequencies vary across species and identify any distinct patterns or differences between them. This visualization provides valuable insights into the variability of petal lengths within the iris dataset and facilitates comparisons between species. Additionally, the histogram illustrates the distribution of sepal width across all observations, complementing our understanding of the dataset’s features.

Visulization 3: Box Plot of Petal Width by Species:

library(ggplot2)
box_plot <- ggplot(data = iris, aes(x = Species, y = Petal.Width, fill = Species)) +
  geom_boxplot() +
  labs(title = "Distribution of Petal Width by Species (Box Plot)",
       x = "Species",
       y = "Petal Width",
       fill = "Species") +
  theme_minimal()
print(box_plot)


This box plot visualizes the distribution of petal widths among different species of iris flowers. It displays the median, quartiles, and potential outliers for each species, allowing for a comparison of the central tendency and spread of petal widths between species. Box plots are useful for identifying differences in variability and central tendency across groups, providing insights into the variability of petal widths within each species.

[5 marks] What might or could you have done differently in question 5 if you were preparing the analysis for another audience/user community?
Answer: Write your answer here:

Tailoring the analysis of the iris dataset for different audience/user communities involves adapting the content, language, and focus to meet their specific needs and interests. if I am preparing the analysis for another audience/user community such as biologists or botanists, the analysis could emphasize the ecological significance of iris characteristics, such as leaf length or flower width, within their natural habitats. For example, discussing how certain iris species with longer leaves may be adapted to drier environments, or how variations in flower width could indicate adaptations for pollination by specific insect species. Additionally, providing insights into conservation efforts related to threatened iris species or the role of irises in ecosystem dynamics could further engage this audience.

On the other hand, if the audience or user community is for students or learners, the emphasis could be on providing a step-by-step explanation of basic data analysis techniques using the iris dataset as an example. This could involve breaking down complex concepts into understandable parts, such as explaining how to calculate summary statistics like mean and standard deviation for iris measurements, or demonstrating how to create simple visualizations like scatter plots to explore relationships between variables. Additionally, including guided exercises where students can apply what they’ve learned to analyze the iris dataset independently, along with links to educational resources for further study, would support their learning journey and development of data analysis skills.

Overall, by tailoring the analysis of the iris dataset to the specific needs and interests of different audience/user communities, we can ensure that the analysis is not only informative but also engaging and relevant to their respective fields or learning objectives for the intended audience.

[8 marks] Your country’s space division recently hired you as a new data analyst. One of your ﬁrst responsibilities is to analyze data on meteorites. In your initial meeting, you reviewed the data and discussed what they wanted to achieve. During this conversation, they revealed that they wanted to locate recent meteorites that have fallen to earth. The goal of this question is to explore the data, decide what story your analysis should tell, and properly organize the data. The data set titled, explore_data.xlsx, has been provided and can be used in R/Tableau to answer the following questions:
• Looking at the data, what two variables do you ﬁnd critical to the analysis? • Can we use the data to map where each meteorite has fallen? • If this is possible, what data ﬁeld is critical for this? • Are there any changes to the data that would make this possible? • Can we determine the largest meteorites that have fallen to Earth? • Each column in the data set was initially created by a computer program. Do these names look correct? Do you see any issues that should be ﬁxed? • Using the provided data, organize each data type into one of the following categories: Qualitative and Quantitative. • For the Quantitative data, highlight discrete values in blue and continuous values in green. To address the questions and prepare the data for analysis:

Answer: Write your answer here:

Looking at the data, what two variables do you ﬁnd critical to the analysis?
Two critical variables for the analysis of recent meteorites would likely be “Date” and “Location.” The “Date” variable allows us to identify recent meteorite falls, while the “Location” variable provides information on where each meteorite fell.
Can we use the data to map where each meteorite has fallen?
Yes, we can use the data to map where each meteorite has fallen.
If this is possible, what data ﬁeld is critical for this?
The “Location” data field, which likely includes latitude and longitude coordinates, would be critical for mapping where each meteorite has fallen.
Are there any changes to the data that would make this possible?
If the “Location” data field does not already include latitude and longitude coordinates, we may need to extract or transform other location information into latitude and longitude format to facilitate mapping.
Can we determine the largest meteorites that have fallen to Earth?
To determine the largest meteorites that have fallen to Earth, we would need to analyze the “Mass” or “Size” data field, assuming it is available in the dataset.
Each column in the data set was initially created by a computer program. Do these names look correct? Do you see any issues that should be ﬁxed?
The column names should be reviewed for clarity and consistency. Any ambiguous or unclear column names should be revised for better understanding. Additionally, if there are any inconsistencies in naming conventions (e.g., mixed case, underscores), they should be standardized.
Using the provided data, organize each data type into one of the following categories: Qualitative and Quantitative?
Qualitative Data:
Categorical variables such as “Name” of meteorite, “Classification” of meteorite, and “Country” of fall.
Quantitative Data:
Discrete Values (highlighted in blue):
Year of fall, which is likely discrete.
Continuous Values (highlighted in green):
Latitude and longitude coordinates for the location of the fall, which are likely continuous.
Mass or size of the meteorite, which is likely continuous.
Perhaps other numerical measurements or characteristics of the meteorites.
By addressing these points, we can better understand and prepare the data for analysis, facilitating the identification of recent meteorite falls, mapping their locations, determining the largest meteorites, and addressing any issues or inconsistencies in the dataset.

[5 marks] Use the file “State_Dept”.xlsx (Data Source: The U.S. State Department’s global list of contracts, http://bids.state.gov/data.html) to nearly recreate the following grey-scale map of average project size by country using Tableau and submit the created map as an image.


Note: For this question export your map as image to take print and submit with Question 1-7. # Load necessary libraries

Answer: Write your code and answer here.

#code
#***********************************

library(ggplot2)
library(readxl)
## Warning: package 'readxl' was built under R version 4.3.2
data <- read_excel("E:/OneDrive - Wilfrid Laurier University/GG501/A1/A1/State_Dept.xlsx")

average_size <- aggregate(project_size ~ Country, data = data, FUN = function(x) mean(as.numeric(x), na.rm = TRUE))
## Warning in mean(as.numeric(x), na.rm = TRUE): NAs introduced by coercion
## Warning in mean(as.numeric(x), na.rm = TRUE): NAs introduced by coercion

## Warning in mean(as.numeric(x), na.rm = TRUE): NAs introduced by coercion

## Warning in mean(as.numeric(x), na.rm = TRUE): NAs introduced by coercion

## Warning in mean(as.numeric(x), na.rm = TRUE): NAs introduced by coercion

## Warning in mean(as.numeric(x), na.rm = TRUE): NAs introduced by coercion

## Warning in mean(as.numeric(x), na.rm = TRUE): NAs introduced by coercion
map <- ggplot(average_size, aes(fill = project_size, map_id = Country)) +
  geom_map(map = map_data("world"), color = "black") +
  expand_limits(x = map_data("world")$long, y = map_data("world")$lat) +
  coord_map() +
  theme_void() +
  theme(legend.position = "right") +
  labs(fill = "Grey Map of Avg Project Size") +
  scale_fill_gradientn(colors = grey.colors(10))
print(map)


To create a map using Tableau, I begin by opening Tableau Desktop on my computer and connect to my data by selecting “Connect to Data” and choosing “state_dept” as the data source type. After browsing to the location of the Excel file and selecting it, the dataset is loaded into Tableau, appearing as an image in the Data Source tab. This allows me to drag the category field from the Data pane to the “Rows” or “Columns” shelf, Customizing the visualization involves adding data points, annotations, filters, and other elements to analyze my data alongside the dataset, creating a new worksheet with diverse visualized graphics. I then edit the color into grey-scale. Finally, I save my work in Tableau format and export it as an image, and name the file name as “Grey Map of Avg Project Size” for sharing and printing, then I generate the Rmarkdown output in html and PDF for submitting the assignment.
