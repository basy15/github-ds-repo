
# Recommander system for Café contractor in Toronto

## PART I

### A description of the problem and a discussion of the background

### Coffee Facts
### Coffee in Canada
Coffee is Canada’s most consumed beverage amongst adults – even more than tap water. As champions for the advancement and enjoyment of coffee in Canada, the Coffee Association of Canada (CAC) continually strives to better understand and educate Canadians about their favourite brew.

Every year, the CAC commissions the proprietary Canadian Coffee Drinking Study on behalf of its members. Below is an infographic, which highlights a few key findings from the results of the 2018 survey.

<a href="http://www.coffeeassoc.com/wp-content/uploads/2018/11/CAC-Coffee-Drinking-Trends-INFOGRAPHIC-2018.pdf">CAC Coffee Drinking Trends INFOGRAPHIC 2018</a>

##### The Coffee Industry in Canada:
    $6.2 billion industry
$4.8 billion sales in Foodservice
    $1.4 billion sales in Grocery / Retail Sales

#### Coffee Creates Jobs in Canada: 

* 160,000+ jobs in Cafes and Coffee Shops

* 5,000+ jobs in Manufacturing and Roasting

* 5,000+ independent café and coffee shop owners and several thousand franchise owner-operators

* Attractive entry-level positions for young people

* Jobs in support sectors such as packaging, cup suppliers, food manufacturing etc.

Given these facts, a New brand of Café contractor wants to spring-up in Toronto, espacially in North York, to provide "Bio" and "Eco" Café to Restaurants. Globally, restaurants don't have a variety of café for their clients and therefore, client get done with one café without any particularities in termes of flavour, taste, aroms, etc. Moreover, Café culture declines a variety of café types by seasons and by origines.

The main idea behind the business is to promote a good quality with divers tastes, all over the seasons, to restaurants so that the "Café" moment become more a deep pleasure thant just appetizers' ends. It's matter of renew with the grand café values. 

This will benefit to restaurants so they will create clients' loyality and retain their actual ones. This will also benefit to the contractor as he will have broad range of customers to supply and make his trademark more known. Consequently, it's win-win business relationship with more income in both parts.

Then the contractor is going to work on this field of the market and find potential restaurants to hold this idea. The geographical scope of the study is Toronto and particularly North York borough where the contractor want to develop first this business.

The contractor should build the store where it is closest to its customers in order to minimize the cost of transporation and supply in short time. Which neighborhood (in that borough) would be a better choice for the contractor to build the store in that neighborhood? The Recommander system should provide this contractor with a sorted list of neighborhoods in which the first element of the list will be the best suggested neighborhood. 



## PART II

### A description of the data and how it will be used to solve the problem

### 1- First, we will collect geographical coordinates information about that specific borough and the its neighborhoods. We assume that it is "North York" in Toronto. This information is given by the contractor, because the contractor has already made up his mind about the borough. The Postal Codes that fall into that borough would also be sufficient.

### 2- We will need data about different venues in different neighborhoods of that specific borough. In order to get that information we will use "Foursquare" location company's dataset. By locational information for each venue we mean basic and advanced information about that venue. For example there is a venue in one of the neighborhoods. As basic information, we can obtain its precise latitude and longitude and also its distance from the center of the neighborhood. But we are looking for advanced information such as the category of that venue and whether this venue is a popular one in its category or maybe the average price of the services of this venue. A typical request from Foursquare will provide us with  the following information:
##### [Postal Code]	[Neighborhood(s)]	[Neighborhood Latitude]	[Neighborhood Longitude]	[Venue]	[Venue Category]	[Distance]
##### [M1L]	[Clairlea, Golden Mile, Oakridge]	[43.711112]	[-79.284577]	[Tim Hortons]	[Coffee Shop]	[592]


### Some Notes about "Foursquare": <https://foursquare.com/>
##### Foursquare is a local search-and-discovery service mobile app which provides search results for its users (Wikipedia).
##### Founded: New York City, New York, U.S
##### Users: 60 million
##### Date launched: March 11, 2009
##### Employees: Over 200
##### Founders: Dennis Crowley, Naveen Selvadurai
##### Owner: Foursquare Labs, Inc.

# Main Article
## Part 1: Identifying Neighborhoods inside "North York"
### We will use Postal Codes of different regions inside North York to find the list of neighborhoods. We will essentially obtain our information from <https://en.wikipedia.org/wiki/List_of_postal_codes_of_Canada:_M> and then process the table inside this site. Images from dataframes and also from maps will be provided in the presentation. Here we only present our strategy and how we got the mission accomplished. 

## Part 2: Connecting to Foursquare and Retrieving Locational Data 
## for Each Venue in Every Neighborhood 
### After finding the list of neighborhoods, we then connect to the Foursquare API to gather information about venues inside each and every neighborhood. For each neighborhood, we have chosen the radius to be 1000 meter. It means that we have asked Foursquare to find venues that are at most 1000 meter far from the center of the neighborhood. (I think distance is measured by latitude and longitude of venues and neighborhoods, and it is not the walking distance for venues.)

## Part 3: Processing the Retrieved Data and Creating a DataFrome for All the Venues inside North York
**When the data is completely gathered, we will perform processing on that raw data to find our desirable features for each venue. Our main feature is the category of that venue. After this stage, the column "Venue's Category" wil be One-hot encoded and different venues will have different feature-columns. After On-hot encoding we will integrate all restaurant columns to one column "Total Restaurants" and all food joint columns to "Total Joints" column. We assumed that different resaturants use the Same raw groceries. This assumption is made for simplicity and due to not having a very detailed dataset about different venues.**

**Now, the dataset is fully ready to be used for machine learning (and statistical analysis) purposes.**

## Part 4: Applying one of Machine Learning Techniques (K-Means Clustering)
**Here we cluster neighborhoods via K-means clustering method. We think that 5 clusters is enough and can cover the complexity of our problem. After clustering we will update our dataset and create a column representing the group for each neighborhood.** 

# Decision Making and Reporting Results
**Now, we focus on the centers of clusters and compare them for their "Total Restaurants". The group which its center has the highest "Total Sum" will be our best recommendation to the contractor. {Note: Total Sum = Total  Restaurants + Total Joints + Other Venues.} This algorithm although is pretty straightforward yet is strongly powerful. **

### Results:
Based on this analysis, the best recommended neighborhood will be:
Neighborhood: Willowdale South,
Postal Code: M2N,
Neighborhood Latitude: 43.770120,
Neighborhood Longitude: -79.408493

### Thanks a lot for reading!
*--------------------------------------------------------------------------*
### Brahim AMRHAR - basy15@gmail.com




```python

```
