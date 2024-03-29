# USDA

The United States Department of Agriculture provides data sets ranging from food
supply, economic demand, and remote sensing through the Agriculture Statistical Service (NASS)
and Economic Research Service (ERS). This application provides an analytics dashboard
and data exploration to help bring to light answers to important questions such as determining
crop yield over time, the relationship to climate change, to simpler questions such as where
food actually comes from.

## Audience

Audience proposed is targeted at end-users typically those who are citizens who have an interest
in the data science and exploration of information reported by the United States Department of Agriculture.
Example websites that may be of concern to such users would be [analytics.usa.gov](analytics.usa.gov), [US Open Data](http://www.data.gov/). The attempt is to modernize the accessibility of this information from isolated toolsets and reports into an interactive web application that anyone can view and explore.

* Citizens of United States
* Data Scientists or Engineers, Analysts
* Agricultural Analysts
* Economists
* Government Officials

The above list of users are typically concerned with seeing and having access to information without having
to dig through lots of reports or text. This application combines various data sets, apis and reports into an interactive feature-set that can be utilized in one stop.

## Design Goals

* Fast, high performance web server continuously downloading the latest data sets
* Visualize United States Food Production
  * Safety, Economic Demand, Preference/Consumption Rates, Yield, Climate Conditions
* Avoid login/signup procedure until further notice of necessity
* Data exploration, visualizations, apis should be public to all users
* To access the api, it may be rate limited at first, use jwt
* Home page should immediately provide the most important visualizations related to USDA datasets
* [analytics.usa.gov](analytics.usa.gov) is a good example of publicly accessibly government data visualized
* Avoid separating content with pages as this jumps users around (potentially too much)
* Illuminate at risk, summarized, answered questions on main page
  * Additional details, search provides more detailed content on a per product basis
* Inform users what the data actually is and where it came from (must reference!)
* Provide users with an application that is an informative tool to existing data, not selling a product
* Using Data and Science to Fight for Truth
  * Hazards of industrial food production practices
  * Pesticides and Insecticides, GMOs
  * Environmental Concerns
  * Climate Change / weather conditions
  * Import/Export Consumptions (are we growing enough of what we eat/consume locally?)
    * What more can we do locally, what grows best in what weather?
* Hold and illuminate bad practice farming techniques
  * EX: Outdated systems
  * EX: Open field growing of thirsty vegetables

## Features / Proposals

* Crop/Fruit/Vegetable/Food dashboard visualizing production, yield, acreage, value, price over time
  * Examples include: Oranges Dashboard
  * Data is available for all of the attributes listed at state and possibly county level
  * Should demonstrate assessment for risk
* Integrate with national weather service or another api
  * Determine if we can store major weather events
    * droughts, extreme rainfall, frost
  * Api for looking up temperature and rainfall over time
  * Some maps on weather.com show frost and drought severity indicators
    * possibly utilize this over time to visualize conditions
* Visualize weather seasonal weather conditions as events
  * Users can make conclusions as to how this affects conditions
  * Ex: no rainfall for significant portion of year
     * Ex vegetable: asparagus weather conditions by state
* Simplified json api for returning data
* Printable reports
* CropScape and/or vegscape map
* Farmers Market Availability (http://search.ams.usda.gov/farmersmarkets/)
  * Crop seasonal availability
  * i.e. Oranges dashboard may reveal in-season availability in farmers markets
    * Map of local markets
    * Quantity by location density over time (heatmap?)
* Notable questions that analysis may reveal:
  * Crop density by location (higher local availability)
  * Crop distribution (less isolated)
  * Crop preference (note declining/increased/consistent utilization)
  * Crop + Farmers market seasonal availability
  * What percentage and where might open-spray irrigation systems be in use?
  * What percentage do we rely on certain crops in isolated locations?
    * Percentage of all crops produced by state
    * Percentage of all crops produced by county
    * Percentage of individual crops produced by state/county
    * Percentage of crops with high dependency (threshold > 90%) produced by state/county
    * With these type of questions on dependency, we can see how reliant industrial farming
    is on certain locations in the United States.
  * Crops produced using poor farming practice and where
    * Open field growing of lettuce/thirsty vegetables better suited for greenhouses
    * Outdated irrigation practices (open air irrigation in hot climates! rather than drip-irrigation systems that provide water directly to the source rather than allow most of the wasted water to be evaporated due to open-air heat)
* Water data
  * Not quite sure where this data is available, but it would be incredible to understand and at least show how much water is consumed due to agriculture, or at least break it down by where its going.
* Nutrition Data
  * http://ndb.nal.usda.gov/ndb/search/list
  * Provide a simple api for showing nutrition information by product
* Pesticides
  * http://www.ams.usda.gov/datasets/pdp/pdpdata
* Recalls
  * http://www.foodsafety.gov/recalls/index.html
* International Food Composition and Resources
  * https://fnic.nal.usda.gov/food-composition/international-food-composition-resources

## Examples

The following are categories of examples pertaining to how we might create a useful dashboard for our users. We want to draw as much as possible from reports generated by the USDA itself. Some common examples in relation to economics, food production and utilization are expanded upon below.

### Farmers Markets, Community Supported Agriculture, Food Hubs and On-Farm Markets

The USDA Farmers Market Directory reveals a database of featured markets that feature two or market farm vendors selling agricultural products to customers at a common, recurrent physical location. The database provides information about where and what products (on a category level) are being sold to customers in addition to the seasonal times and availability. While more significant details on quantity may not be available, it may be useful to use this database for demonstrating local market availability when it season on a per commodity basis. We can visualize this information by showing either a heatmap or simple search map for local markets that may have the products users are looking for. Additionally the service provides a directory listing for Community Supported Aggriculture (CSA) http://search.ams.usda.gov/CSA/, food hubs, and on-farm markets (http://www.usdalocalfooddirectories.com/listings.html). All of these can be aggregated and provided through an easy to use search/api.

### Local Harvest

Local Harvest (http://www.localharvest.org/) is a community of local families and farming communities with over 30,000 listings around the United States. This listing may be helpful but may potentially overlap with other directories. It may be worth exploring further as it contains more detailed information about the products available from various local communities.

### CropScape

CropScape (http://nassgeodata.gmu.edu/CropScape/) is a layer for visualizing the cropland data layer created from remote sensing sattelites. The particular application shown in the link demonstrates the ability to select areas on the map and query for particular crop acreage. The tool also visualizes crop acreage on a pixel level and using a color chart to denote various crop types. Statistic tools are provided to show estimations on pixel count to acreage for various types of land discovery. The tool provides filtering capabilities on regions, state level, county..etc. The tool will draw regions around the selected filter and allow the user to see statistics for that area while color coding individual pixels accordingly. The tool however does **lack** the ability to filter on a crop level (i.e. I only want to see corn pixels). The tool will allow the user to show all this on a yearly basis. The data seems to only improve in resolution as time moves on - making historical analysis not all that useful unfortunately. The tool also provides a swipe allowing the user to see the visual difference between two different points in time.

### VegScape

VegScape (http://nassgeodata.gmu.edu/VegScape/) is a layer for visualizing vegetation conditions over time. The tool actually provides the ability to show vegetation conditions in various formats over time in a bi-weekly or even daily time period. Formats depend on the use but the following (http://www.star.nesdis.noaa.gov/smcd/emb/vci/VH/) demonstrates that VCI (vegetation condition index). (Note: NOAA actually includes the ability to generate animations on a daily basis for these types of formats and others including fire risk..etc). The animation on the the page demonstrates the effects over time of usable vegetation. VegScape provides various formats including:

* NDVI - Normalized Difference Vegetation Index

```
The Vegetation Condition images are created in two types, NDVI and Ratio. NDVI (Normalized Difference Vegetation Index) images are directly based on values created by the USGS's EROS Data Center in their biweekly composite [3] of AVHRR sensor data from one of the NOAA weather satellites. Prior to 1995, the NOAA-11 satellite was the source for AVHRR data. From 1995 to 1999, the NOAA-14 satellite provided AVHRR sensor coverage, but this satellite/sensor failed in 2000. Starting in 2001, the NOAA-16 satellite began providing AVHRR data for this data series. NOAA-16 started malfunctioning in 2004, with a scan motor problem. Images from NOAA-17 are used beginning with the 2004 season.

The NDVI measures vegetation vigor caused by chlorophyll activity; this is sometimes called "greenness". These data have proven valuable to USDA policy officials in providing geographic location and monitoring information for vegetation condition in crop areas. NDVI values can theoretically range from -1 to +1; high values represent healthy, vigorous vegetation while low values typically depict bare soil and water.

Ratio images compare current NDVI values to NDVI values from some previous period; these comparisons are expressed at NASS in the form of a percent change. There are two comparison ratios that can be created, a percent change from closest corresponding dates of the previous year plus a percent change from the median value of the corresponding periods from the previous three years (when 3 comparable years are available).
```

### Citrus Fruit

An example report is provided by the USDA on Citrus Fruit. (http://usda.mannlib.cornell.edu/usda/current/CitrFrui/CitrFrui-09-18-2014.pdf). This report specifies details in relationship to the following:

* Utilized Citrus Production (over 2004-2014)
* Citrus Value of Production (over 2004-2014)
* Citrus Acreage and Bearing
* Citrus Type Yield
* Citrus Type Price

Typically these are broken down by the citrus fruit type such as oranges, grapefruits, lemons..etc. Each item details the bearing acreage, production (total, fresh, processed), value of production, yield per acre, utilization, price per box (all, fresh, processed). Simple graphs detailing individual food types will show some fairly significant trends such as the total bearing acreage over time in steady decline. By visualizing these items we may be able to show a very simple extrapolation to show if and when the particular food items are at risk for depletion.

In addition, production and utilization is noted according to the state and possibly county level. By leveraging this particular data set, we can visualize the percentage of production and utilization over time with reference to a given state. If for instance, 100% of a particular fruit happens to be produced by a single state or area and over time that area is in decline - conclusions can be drawn by the user as to the reasons why that is. For instance, if year after year yield is becoming less and less, while utilization remains steadily the same - we can conclude that our consumption is not the reason it is running out and perhaps climate may be a factor, or pests or other concerns.

### Vegetables

Vegetable production reports demonstrate similar attributes to yield, production, utilization, value and acreage as citrus fruit categories. A sample report (http://usda.mannlib.cornell.edu/usda/current/Vege/Vege-09-04-2014.pdf) shows various food items and their reports over time. Additional comments are made with respect to individual food items about food production in relationship to climate conditions. For example, the report notes a decade long decline for asparagus acreage. We should be able to easily determine these trends without much effort using a standard linear regression model over expected acreage, yield and utilization. Since these items are perishable, stockpile is somewhat irrelevant and thus a contining decline in yield demonstrates risk for depletion.

Additional notes are made in the report with respect to weather conditions. Specifically, drought conditions and lack of rainfall during various seasons has a significant impact on crop production. We should be able to utilize the national weather service to show conditions for rainfall over time and determine whether a decline in production is related (otherwise, our visualizations should be able to note and simply graph rain conditions over time for a specific state as a sidenote.) In fact, many of the comments on the sample report note weather conditions affecting crop production (such as frosting during certain months, heavy rains during an off season..etc.
