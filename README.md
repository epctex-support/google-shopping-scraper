# Actor - Google Shopping Scraper

## Google Shopping scraper

Google Shopping Scraper will enable you to extract product data from Google Shopping under any country domain. It scrapes the result pages and details about each product and its sellers.

-   Search any keyword - You can search for any keyword you would like to have and get the results.

-   Scrape reviews and rating - Scrape product reviews and rating without any limitation.

-   Scrape product detail - Get all the information that is available on Google Shopping.

-   Scrape merchant names and links - Merchant names, affiliation and product links will be available for you.

- Retrieve all the compared prices from different websites and merchants!


## Why scrape Google Shopping?
Google Shopping is a great source of data for basically any industry. From clothes to tech, it's a great place to extract data for market research and price monitoring.

Here are just some of the ways you could use that data:
- **Market Research**: See what products are on the market, and analyze them to discover how to market your own products. Find out who your competitors are and make sure there is a market for your product.
- **Price Monitoring**: Find the perfect deal by regularly extracting prices. See how your competitors how pricing their products and create your own winning dynamic pricing strategy.
- **Product Research**: If you're waiting for a product to be available again, scrape regularly to be the first to know as soon as you can purchase it, or get insights into what's on the market so you can develop your own products.

## Bugs, fixes, updates and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/google-shopping-scraper/issues).

## Input Parameters

The input of this scraper should be JSON containing the list of pages on Google Shopping Scraper that should be visited. Possible fields are:

- `search`: (Optional) (String) Keyword that you want to search on Google Shopping.

- `startUrls`: (Optional) (Array) List of Google Shopping URLs. You should only provide only search pages from Google Shopping.

- `includeComparisonPrices`: (Optional) (Boolean) This option will enable the actor to retrieve all the possible prices from other merchants with comparison.

- `includeReviews`: (Optional) (Boolean) This will add all the reviews that XXXXX provides into the detail objects. Please keep in mind that the time and resources the actor uses will increase proportionally by the number of reviews.

- `maxItemsPerQuery`: (Optional) (Number) You can limit scraped products per each query. This should be useful when you search through the big lists.

- `maxItems`: (Optional) (Number) You can limit scraped products. This should be useful when you search through the big lists or search results.

- `proxy`: (Required) (Proxy Object) Proxy configuration.

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

### Tip

When you want to have a scrape over a specific listing URL, just copy and paste the link as one of the **startUrl**.

### Compute Unit Consumption

The actor optimized to run blazing fast and scrape many as listings as possible. Therefore, it forefronts all listing detail requests. If actor doesn't block very often it'll scrape 100 listings in 2 minutes with ~0.05-0.1 compute units.

## Tips for scraping Google Shopping
Here's a tip for scraping Google Shopping. If you want to filter your search by product details (price range, color, model, etc), head over to the Google Shopping website in a separate browser window, type your keyboard into the search bar, and toggle with the filters. Once you are done, copy the web page's URL, and paste it into the scraper's input field!

### Google Shopping Scraper Input example

```json
{
  "queries": [
    "iPhone"
  ],
  "maxItems":80,
  "countryCode": "us",
  "includeComparisonPrices":true
  "startUrls":[
    "https://www.google.com/search?q=android&source=lnms&tbm=shop&tbs=vw:l"
  ],
  "proxy":{
    "useApifyProxy":true,
    "apifyProxyGroups":[
      "GOOGLE_SERP"
    ]
  }
}
```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of what is wrong.

## Google Shopping Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Google Shopping actor.

## Scraped Google Shopping Properties

The structure of each item in Google Shopping looks like this:

```json
{
	"productName": "Willow & Silk Colour Birds w/ Home 3 Bells Hanging",
	"productLink": "http://www.google.com.au/shopping/product/13169701087423086284?q=06934BEL&gl=AU&prds=eto:57679750986077523_0,pid:11810335896967482237,rsk:PC_12136905723812258232&sa=X&ved=0ahUKEwj3sPzCitT-AhVORjABHQwaBvUQ8gIIYw",
	"price": "$34.95",
	"withoutDiscountPrice": "$49.95",
	"description": "Outdoor · Metal · Iron",
	"merchantName": "Temple & Webster",
	"merchantLink": "http://www.google.com.au/url?q=https://www.templeandwebster.com.au/Birds-with-Home-Iron-Hanging-Bells-HSTR2931.html%3Frefid%3DGPAAU447-HSTR2931&sa=U&ved=0ahUKEwip1t3MitT-AhUKMVkFHTZzB_gQ2ykIRg&usg=AOvVaw05H6-jDtCPDYz-5EuPG8JN",
	"shoppingId": "13169701087423086284",
	"reviewsScore": "5.0",
	"reviewsCount": "2",
	"positionOnSearchPage": 1,
	"productDetails": "Add some French country charm to your front porch, garden, patio or courtyard with Birds Home 3 Hanging Bells. Crafted from ...",
	"totalPrice": "$45.90"
}
```
