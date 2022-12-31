![cover](https://github.com/heathlikethecandybar/phase_3_project/blob/main/phase_3/project/images/DALL%C2%B7E%202022-12-31%2009.32.25%20-%20pattern%20identification%20using%20ai.png)

# Skyvia Telcom Customer Churn Classification

**Author**: [Heath Rittler](mailto:hrittler@gmail.com)


## Overview

https://www.kaggle.com/datasets/becksddf/churn-in-telecoms-dataset

Build a classifier to predict whether a customer will ("soon") stop doing business with SyriaTel, a telecommunications company. This is a binary classification problem.

Most naturally, your audience here would be the telecom business itself, interested in reducing how much money is lost because of customers who don't stick around very long. The question you can ask is: are there any predictable patterns here?


## Business Problem

Acquring a new customer on average costs 3x that of retaining an existing customer.  At Skyvia, they are trying to optimize their retetention strategies, and do to so they are trying to understand what features of different customers indicate churn.  The presentation will be made availble for the VP of Customer Success, and the Chief Revenue Officer.




## Data

This project uses the King County House Sales dataset, which can be found in  `kc_house_data.csv` in the data folder in this repository. The description of the column names can be found in `data_dictionary.md` in the same folder.  The dataset includes 21,597 entries, and 21 columns.  Here are the columns in the dataset:

* `id` - Unique identifier for a house
* `date` - Date house was sold
* `price` - Sale price (prediction target)
* `bedrooms` - Number of bedrooms
* `bathrooms` - Number of bathrooms
* `sqft_living` - Square footage of living space in the home
* `sqft_lot` - Square footage of the lot
* `floors` - Number of floors (levels) in house
* `waterfront` - Whether the house is on a waterfront
* `view` - Quality of view from house
* `condition` - How good the overall condition of the house is. Related to maintenance of house.
* `grade` - Overall grade of the house. Related to the construction and design of the house.
* `sqft_above` - Square footage of house apart from basement
* `sqft_basement` - Square footage of the basement
* `yr_built` - Year when house was built
* `yr_renovated` - Year when house was renovated
* `zipcode` - ZIP Code used by the United States Postal Service
* `lat` - Latitude coordinate
* `long` - Longitude coordinate
* `sqft_living15` - The square footage of interior housing living space for the nearest 15 neighbors
* `sqft_lot15` - The square footage of the land lots of the nearest 15 neighbors

Additional information about this dataset can be found on the [King County Assessor Website](https://info.kingcounty.gov/assessor/esales/Glossary.aspx?type=r) Accessor Website. 


## Methods




## Results

The first view we took was looking at our average and median price for homes over time.  The dataset has a pretty broad range of homes, starting in 1990 all the way until 2015.  Being that we are focusing on a higher r2 value, to normalize the data, we began our analysis by pulling only the records from 1990 and after.  This gives us a much more normal distribution of price data, giving us better result when we look at our model's performance. 

The median home value for King County during this time period is $475k.  So homeowners will quickly be able to assess where the perceived value of their home stands in comparison. This to say that houses with this median home value, also have 2,240 square foot of living area, 2.5 bathrooms, and an median grade number of 7.  Which are features we will continue to evaluate in our model as impactable features.  This information will also be helpful for clients to compare where their current home is based on the build year to what we have in this visual.  With that being said, clients with a home that is older than 1990, can use the statistical values as a comparison for now.  I have also broken out older home values for more specifics, however less accurate, if the client so chooses to use an additional comparison.

![median_home_value_over_time](https://github.com/heathlikethecandybar/dsc-phase-2-project-v2-3/blob/main/images/median_home_value_over_time.png)

Now that we understand the typical home in King County, let's take a look at a few different ideas that we can suggest to our clients.  These are enhancements that the client could make at their discretion.  The first feature is square footage of living space.  The median value of square footage in King County is 2,240.  A homeowner would be able to increase their home by $101 per square foot that they add to the footprint of their home.  Remember that living space or area is defined as a part of the home that is heated or cooled, similar to a dining room, or a kitchen for example.  So a customer could increase the value of their home by $10,100 if they were to add a 10x10 room to the overall foot print.  Depending on the grade of the home, and of the room added, could also depend on the impact/ value added when constructing the addition.  These data points should also be considered when evaluating the ultimate build and return on investment when thinking about these types of projects.  In the chart below, you can see the positive association between the price of a home, and the square footage of living space that the home represents.

![sq_ft_price_scatter](https://github.com/heathlikethecandybar/dsc-phase-2-project-v2-3/blob/main/images/sq_ft_price_scatter.png)

In addition to square footage of living space, the next value add to a home owner is 1/4 bathrooms.  1/4 bathrooms can be defined as any component of the bathroom if you think of them individually.  So a toilet, a sink or washbasin, and a shower, and a bathtub would represent a full bathroom.  Adding any one of these components to your bathroom would add an additional $21k of value to your home.  Now considering that smaller bathrooms may not have enough size to evolve into a full bathroom, but most bathrooms could handle adding a sink or washbasin, or a toilet depending on how the bathroom is set up.  We don't necessarily know the combination of the bathrooms in this dataset, so we wouldn't be able to recommend which line up yields the most value.  The clients could however, reference the chart below to understand where their bathroom is, and the potential increment if they were to increase the features within their bathroom.

![baths_round_hbar](https://github.com/heathlikethecandybar/dsc-phase-2-project-v2-3/blob/main/images/baths_hbar.png)

Another features that was evaluated but didn't spend a lot of time on is the grade of the home.  The grade is a scale from 0-13 that represents the overall quality of the home, and an evaluation of the materials used when the home was built.  Each grade that a homeowner can increase the qualitfy of their home, they can add an addition $99k value.  We choose not to fully include this as a part of the recommendation set, but can be used as an alternative recommendation if the first 2 recommendations do not work out for the customer.  Since the home is already built, this feature would apply to the finishes, and final touches of the home, which would manifest in home improvements in all aspects of the home.


## Conclusions

In conclusion, we were able to evaluate and identify a few different options for our customer and ultimately some recommendations that they can make to the clients about increasing the value of their home.  In summary those features are:

- **The median home price in King County, WA is $475k**
- **By increasing the living square footage of your home, you can increase the value by $101 per square foot.** 
- **By adding bathrooms, and adding 1/4 bath features, you can increase the value of your home by $21k for each 1/4 bath you add.** 



## Moving Forward

Further analyses in these areas could yield additional insights

- **Address limitations/ concerns - add additional pricing data, adjust for inflation, etc.**
- **Look at additional zip codes to understand values more specifically (or not).**
- **Evaluate additional variables/ features such as environmental, or other factors that may have an impact on a home’s value.**
- **Refresh the analysis regularly with new data to understand how the market is evolving over time.**


## For More Information

The full analysis is located in the [Jupyter Notebook](./phase_2_project.ipynb) or review this summary [presentation](./phase_2_presentation.pdf).

For additional info, contact Heath Rittler at [hrittler@gmail.com](mailto:hrittler@gmail.com)


## Repository Structure

```
├── data
├── images
├── README.md
├── phase_2_presentation.pdf
├── phase_2_notebook.pdf
└── phase_2_project.ipynb
```


cover photo credit:  OpenAI labs - Dall-E created on 12/31/2022