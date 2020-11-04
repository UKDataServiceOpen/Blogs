# Working With Data

[Python](https://www.python.org/)  and [R](https://www.r-project.org/) are the main tools in the world of data. Although they aren't trivial to get started with, they should be. This post walks through my day 1 set up at the [UK Data Service]( https://ukdataservice.ac.uk/). This post covers setting up any machine for Python, R and a plotting example for each. No programming knowledge needed.
 
The UK Data Service hosts the United Kingdom's largest collection of social data. Through the website, you can request, manage and deposit all sorts of social data. Sharing access to that data is only the first step. To make an impact we need people of all skill levels to explore that data.
 
## Setup
I will get to my recommendations shortly. If you are looking to install Python or RStudio then here are the relevant links:
* [RStudio](https://rstudio.com/products/rstudio/download/)
* [Python](https://www.python.org/downloads/windows/)
 
If you are on a Windows device you likely don’t have Python installed.
 
If you are on a device running macOS or anything Linux based it’s likely you already have Python installed. You can check this by running the `python` or `python3` command in your terminal. If you aren’t familiar with the terminal that’s fine too, let’s look at some alternatives.

## Alternative Python & R
Often we want a way to run our code without needing to know about the command line. Below are alternatives that let you write code without learning more tools.

### REPL.IT
![Screenshot of REPL.IT text editor and terminal](https://github.com/joseph-allen/Blogs/blob/master/WorkingWithData/images/REPL.JPG)

[Repl.it](https://repl.it/) lets you create disposable environments for Python, R and much more. This is a great place to quickly write simple code, explore a small dataset, try out packages and share your code publicly.

### Google Colab
![Screenshot of Google Colab notebook](https://github.com/joseph-allen/Blogs/blob/master/WorkingWithData/images/GoogleColab.jpeg)

[Google Colab](https://colab.research.google.com/notebooks/intro.ipynb) lets you run code in the browser in notebook style. A notebook is a collection of code alongside markdown cells. This format lets you write textual analysis inline with code fragments. This, in turn, helps make your work more reproducible and understandable. One disadvantage is that Colab uses Google Drive to store your data. Viable alternatives here are Jupyter or JupyterLab.

### Anaconda
[Anaconda](https://www.anaconda.com/)  is a Data Science platform that includes Jupyter, RStudio and more. Anaconda handles managing environments and package installation. This keeps us away from the worst the command line has to offer.

## Anaconda Setup
First of all download the Anaconda version for your Operating System. Downloads are available [here](https://www.anaconda.com/products/individual#Downloads). Run the installer, this should take about 10 minutes.

Once installed, run anaconda and you should see something like the below. You should have access to Jupyter, JupyterLab, RStudio, VS Code and more. You may have to install these if you want to use them. The most common program I use here is JupyterLab.

## Versioning & Packages
While early project work might be simple, often you need to use a more recent version of a package. You may need to downgrade your Python version to reproduce a project from years ago. Anaconda makes this easy with the “Environments” tab. Here you can create, swap between and manage your environments. This is where you come if you need to install a new package. If you plan on writing R, create a new environment now with both a Python and an R library.
 
## A tiny project
To show what we can do in JupyterLab lets work through a small project.  Download the following [Airbnb data]( https://www.kaggle.com/kritikseth/us-airbnb-open-data ). The following will guide you through reading and displaying data.

## Display Data - [Python Demo](https://github.com/joseph-allen/Blogs/blob/master/WorkingWithData/Demo.ipynb)
![Screenshot of a JupyterLab notebook](https://github.com/joseph-allen/Blogs/blob/master/WorkingWithData/images/Anaconda.png)
First of all Launch JupyterLab, if this is not installed do so now. If this works it will open a JupyterLab tab in your default browser. In the left-hand side of this tab, you should see a file browser, navigate to wherever you’d like to save your notebook.  Create a new Python 3 notebook. This will have a default filename of "Untitled.ipynb". Rename this if you like.
 
![Screenshot of a JupyterLab notebook](https://github.com/joseph-allen/Blogs/blob/master/WorkingWithData/images/AnacondaNotebook.png)

You can also drag and drop your dataset into the file browser to upload it to your session. Again rename this dataset if you like, in my example code, I’ve called it `data.csv`. You should now have both your notebook and a dataset available.

If you double click the dataset you will see an Excel-like table of your data. This can be useful to check your data is as expected, and ask any data quality questions.
![Screenshot of a Data in a table format in JupyterLab](https://github.com/joseph-allen/Blogs/blob/master/WorkingWithData/images/AnacondaData.png)

There is a small “plus” icon next to the save button for your .ipynb file, this will let you create new cells. And the “Code” dropdown will let you swap between markdown and code for this cell. In our first cell we can write:

```
# Import pandas, our data manipulation library
import pandas as pd

# Read our dataset into a dataframe
df = pd.read_csv("data.csv")

# Print out the first 5 records
df.head()
```

This imports our data manipulation library and reads our data. Finally, we print the first 5 records. Now make another Code cell and past in the following:

```
# Plot the number of airbnbs in the top 5 cities.
df['city'].value_counts().head(5).plot(kind='bar')
```

This should plot a bar chart of the five cities with the most Airbnb’s, and the number of Airbnb’s in each city.

## Display Data - [R Demo](https://github.com/joseph-allen/Blogs/blob/master/WorkingWithData/Demo-R.ipynb)
Writing R code in Jupyter requires we create an R notebook. We need a new environment which has both Python and R installed.  To do this go to the “Environments” tab and create a new environment with a Python and an R version installed. This may take up to ten minutes.  

IMAGE

If you prefer here, you have the option of installing and running RStudio from Anaconda. I recommend giving JupyterLab a go though! You may need to install JupyterLab again for this new Python and R environment. First of all Launch JupyterLab. In the left-hand side of this tab, you should see a file browser, navigate to wherever you’d like to save your notebook. Create an R notebook, and rename this from the default “Untitled.ipynb”.

My R is much sloppier than my Python so apologies if I’ve missed anything obvious here. 

There is a small “plus” icon next to the save button for your .ipynb file, this will let you create new cells. And the “Code” dropdown will let you swap between markdown and code for this cell. In our first cell we can write:

```
# Import ggplot2, our data visualization library
library(ggplot2)
library(tidyverse)
```

This imports our plotting and data manipulation libraries. Next in another cell let’s read our data into a dataframe:

```
# Read our dataset into a dataframe
df <- read.csv(file = 'data.csv')

# Print out the first 5 records
head(data)
```
This should print out the first five records too. Next let’s count the number of Airbnb’s in each city:

```
# create a new table of the number of airbnbs in each city
counts <- df %>% count(city)
head(counts)
```

And finally let’s plot a graph of the top 5 most Airbnb populated cities in this dataset:

```
# Sort by number of airbnbs, and return the top 5 results.
sortedCounts <- head(counts %>% arrange(desc(n)), n=5)

# plot a bar chart
ggplot(data=sortedCounts, aes(x=city, y=n)) +
  geom_bar(stat="identity")
```
## GitHub - Share your work
While I haven’t covered what git and GitHub are in this post, I will save this for a later blog post. For now, know that GitHub is a place to store programming related files. One extra benefit of Jupyter Notebooks is that Github will render them. This means that whatever you save and push to GitHub can be public or private. See the following examples:
* [Python Demo](https://github.com/joseph-allen/Blogs/blob/master/WorkingWithData/Demo.ipynb)
* [R Demo](https://github.com/joseph-allen/Blogs/blob/master/WorkingWithData/Demo-R.ipynb)

## Next Steps
So we’ve set up our environment to do some basic data science. What comes next is the answer to two questions:
* Where can I find data?
* Where can I learn Python and R?

## Data Sources
### UK Data Service
The UK Data Service holds the UK’s largest collection of social data. They have a useful [key data page](https://www.ukdataservice.ac.uk/get-data/key-data.aspx) which hosts some of their most popular datasets.

### Kaggle
Kaggle host Machine Learning Competitions. Kaggle has expanded to offer tutorials, datasets and host well-documented analysis. Kaggle host some open data [here](https://www.kaggle.com/datasets). The data used in this post is the [Airbnb open dataset](https://www.kaggle.com/kritikseth/us-airbnb-open-data).
 
## Continue Learning
### Codecademy 
Codecademy is a great way to practice the fundamentals of languages. They offer a Data Science Career path, and courses in Python and R. If you are a student you can get 35% off.
Course pages:
* [Python](https://www.codecademy.com/learn/learn-python-3)
* [R](https://www.codecademy.com/learn/learn-r).
* [Data Science career path](https://www.codecademy.com/learn/paths/data-science).

### DataCamp
[DataCamp](https://www.datacamp.com/) is like Codecademy, but with a larger focus on data. They offer Python, R and a Data Science career track as well. Some lessons are free. DataCamp is free if you set it up as an educator with [DataCamp for Schools](https://www.datacamp.com/groups/education).

### LearnXInYMinutes
As both the above need payment, this is our free option. This website helps programmers transition from one language to another. Each supported language has a single page full of practical examples. They have pages for:
* [Python](https://learnxinyminutes.com/docs/python/) 
* [R]( https://learnxinyminutes.com/docs/r )

Thanks for reading and good luck.
