# housing_listings

### Problem Area

For this project, we are going to look at the U.S. housing market and, more specifically, at the housing market in Austin, Texas. While our data is location specific, the idea is that the data preparation and modeling procedures developed as part of this project can be replicated to apply to any geography. Predicting housing prices would allow both sellers and buyers to define the appropriate house price in order to do a transaction on the market. Price predictor may also allow governments and other related agencies to make housing price predictions to assess the current state of the housing market.

### Dataset and Preprocessing

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




- A non-technical overview of the problem statement, your proposed solution, and an estimate of the potential impact of your solution.
- An overview of the dataset and preprocessing procedures
- A few important findings from EDA
- Baseline models and evaluation metrics
- Next steps for advanced modeling and productizing your work

