# housing_listings

### Problem Area

For this project, we are going to look at the U.S. housing market and, more specifically, at the housing market in Austin, Texas. While our data is location specific, the idea is that the data preparation and modeling procedures developed as part of this project can be replicated to apply to any geography. Predicting housing prices would allow both sellers and buyers, as well as their realtors to define the appropriate house price in order to do a transaction on the market. Price predictor may also allow governments and other related agencies to make housing price predictions to assess the current state of the housing market.

### Dataset Overview

The dataset was obtained from Kaggle: https://www.kaggle.com/datasets/ericpierce/austinhousingprices/data. It contains 2.52 GB of data, however, most of that space is occupied with photos of the houses. The CSV file contains 11.86 MB of data. There are 47 features (including our dependent feature - latest price. The database has 15,171 rows. The features are as follows:

- zpid: Unique Identifier - Zillow Property ID
- city: The lowercase name of a city or town in or surrounding Austin, Texas
- streetAddress: The street address of the listing
- zipcod: The listing 5-digit ZIP code
- description: The description of the listing from Zillow
- latitude: Latitude of the listing
- longitude: Longitude of the listing
- propertyTaxRate: Property Tax Rate for the listing
- garageSpaces: Number of garage spaces. This is a subset of the ParkingSpaces feature
- hasAssociation: Indicates if there is a Homeowners Association associated with the listing
- hasCooling: Boolean indicating if the home has a cooling system
- hasGarage: Boolean indicating if the home has a garage
- hasHeating: Boolean indicating if the home has a heating system
- hasSpa: Boolean indicating if the home has a Spa
- hasView: If the home comes with a view, determined by the property lister
- homeType: The home type (i.e., Single Family, Townhouse, Apartment)
- parkingSpaces: The number of parking spots that come with a home
- yearBuilt: The year the property was built
- latestPrice: The most recent available price at time of data acquisition
- numPriceChanges: The number of price changes a home has undergone since being listed
- latest_saledate: The latest sale date (YYYY-MM-DD)
- latest_salemonth: The month the home sold (1-12)
- latest_saleyear: The year the property sold (2018-2021)
- latestPriceSource: The party that provided the sale price
- numOfPhotos: The number of photos in the Zillow listing. Only the first photo is included in the homeImages folder
- numOfAccessibilityFeatures: The number of unique accessibility features in the Zillow listing
- numOfAppliances: The number of unique appliances in the Zillow listing
- numOfParkingFeatures: The number of unique parking features in the Zillow listing
- numOfPatioAndPorchFeatures: The number of unique patio and/or porch features in the Zillow listing
- numOfSecurityFeatures: The number of unique security features in the Zillow listing
- numOfWaterfrontFeatures: The number of unique waterfront features in the Zillow listing
- numOfWindowFeatures: The number of unique window aesthetics in the Zillow listing
- numOfCommunityFeatures: The number of unique community features (community meeting room, mailbox) in the Zillow listing
- lotSizeSqFt: The lot size of the property reported in Square Feet
- livingAreaSqFt: The living area of the property reported in Square Feet
- numOfPrimarySchools: The number of Primary schools listed in the area on the Zillow listing
- numOfElementarySchools: The number of Elementary schools listed in the area on the Zillow listing
- numOfMiddleSchools: The number of Middle schools listed in the area on the Zillow listing
- numOfHighSchools: The number of High schools listed in the area on the Zillow listing
- avgSchoolDistance: The average distance of all school types (i.e., Middle, High) in the Zillow listing
- avgSchoolRating: The average school rating of all school types (i.e., Middle, High) in the Zillow listing
- avgSchoolSize: The average school size of all school types (i.e., Middle, High) in the Zillow listing
- MedianStudentsPerTeacher: The median students per teacher for all schools in the Zillow listing
- numOfBathrooms: The number of bathrooms in a property
- numOfBedrooms: The number of bedrooms in a property
- numOfStories: The number of stories a property has
- homeImage: The name of the first image from the home listing. This image file can be found in the included homeImages folder

Number of features after feature engineering and cleaning (done in the following steps) increases to 54. The housing listings are obtained from Zillow and are scraped as of January 2021.

### Preprocessing and EDA

As the next step, we investigated the data further. It contained no duplicates and only a few missing values in the description column. Because the missing values were very few (2), we have removed the rows that contained them. Further, we have looked at the geographic map of housing properties and identified that the properties generally cluster by price, with those <$309k (1st quartile of the distribution) located on the east side of the city, those between $309k and $405k (where $405k is the median value) spread in the middle of the city, from north to south, and those >$405k located in the central and western edge of the city.  

Later in our analysis, we have revealed that our dependent variable (Price) has outliers going up to $13.5M. We have then chose to eliminate the outliers and run some of the regression models on data only including rows with housing prices between $100k and $500k. 

We have then dropped a few features that industry knowledge would suggest to be non-meaninful or that were duplicative of other features. Next steps included creating dummy variables, converting boolean to numerical values.

### Baseline Models and Evaluation Metrics

We run three models - linear regression, decision tree regressor, and KNN regressor. For linear regression, we first went through the steps of removing features when there was correlation >50% between features (that was an iterative process). Afterwards, we checked for multicollinearity using Variance Inflation Factor (VIF) and removed variables with VIF >5. We ended up with 10 independent variables suitables for regression analysis (not a large number). We ran the linear regression on the dataset before removing outliers, which resulted in -43% test score. We subsequenly ran a regression on the data after removing outliers, which resulted in 15% test score.

Subsequently, we ran a decision tree regressor before and after removing outliers on 54 independent features. The model gave 47% test score before removing outliers and 45% score after removing outliers. We have identified that depth of 7 was the most appropriate hyperparameter for the model excluding outliers (and depth of 3 before excluding outliers).

When running KNN regressor, we have received test score of 49% (before removing outliers). That is based on n_neighbours of 10, our calibrated hyperparameter. When we exclude outliers, test score equals to 39% (n_neighbours of 10 as well). We tried to optimize for hyperparameter “weights” for KNN Regressor. Setting hyperparameter "weights" to "distance" (meaning that closer neighbors will have more influence on the prediction than farther ones) makes the model overfit. By default, weight is uniform, and we are keeping it as such.

### Conclusion

As our analysis revealed, the best peforming models, as measured by test scores, are: (1) Decision Tree - with 47% R^2 score without excluding outliers and (2) KNN Regressor - with 49% R^2 score without excluding outliers. While the test score of ~50% is not too high as an absolute value, we are satusfied with it for our purpose. The result proves that pricing houses is a combination of art & science, and the model we have developed, along, would not be sufficient to accurately determine prices (would likely need human interference).
