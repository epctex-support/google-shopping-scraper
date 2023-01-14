# Actor - Google Shopping Scraper

## Google Shopping scraper

Google Shopping Scraper will enable you to extract product data from Google Shopping under any country domain. It scrapes the result pages and details about each product and its sellers.

-   Search any keyword - You can search for any keyword you would like to have and get the results.

-   Scrape reviews and rating - Scrape product reviews and rating without any limitation.

-   Scrape product detail - Get all the information that is available on Google Shopping.

-   Scrape merchant names and links - Merchant names, affiliation and product links will be available for you.


## Why scrape Google Shopping?
Google Shopping is a great source of data for basically any industry. From clothes to tech, it's a great place to extract data for market research and price monitoring.

Here are just some of the ways you could use that data:
- **Market Research**: See what products are on the market, and analyze them to discover how to market your own products. Find out who your competitors are and make sure there is a market for your product.
- **Price Monitoring**: Find the perfect deal by regularly extracting prices. See how your competitors how pricing their products and create your own winning dynamic pricing strategy.
- **Product Research**: If you're waiting for a product to be available again, scrape regularly to be the first to know as soon as you can purchase it, or get insights into what's on the market so you can develop your own products.

## Bugs, fixes, updates and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/google-shopping-scraper/issues).

## Input Parameters

The input of this scraper should be JSON containing the list of pages on Google Shopping Scraper that should be visited. Required fields are:

| Field                | Type    | Description                                                                                                                                                                                                    |
| -------------------- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| search               | String  | (optional) Keyword that you want to search on Google Shopping.                                                                                                                                                       |
| startUrls            | Array   | (optional) List of Google Shopping URLs. You should only provide only search pages from Google Shopping.                                                                                                                 |
| maxItems             | Integer | (optional) You can limit scraped products. This should be useful when you search through the big lists.                                                                                                |
| proxy                | Object  | Proxy configuration                                                                                                                                                                                            |

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

##### Tip

When you want to have a scrape over a specific listing URL, just copy and paste the link as one of the **startUrl**.

### Compute Unit Consumption

The actor optimized to run blazing fast and scrape many as listings as possible. Therefore, it forefronts all listing detail requests. If actor doesn't block very often it'll scrape 100 listings in 2 minutes with ~0.05-0.1 compute units.

## Tips for scraping Google Shopping
Here's a tip for scraping Google Shopping. If you want to filter your search by product details (price range, color, model, etc), head over to the Google Shopping website in a separate browser window, type your keyboard into the search bar, and toggle with the filters. Once you are done, copy the web page's URL, and paste it into the scraper's input field!

### XXXXX Scraper Input example

```json
{
  "queries": [
    "iPhone"
  ],
  "maxItems":80,
  "countryCode": "us",
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
	"productName": "Apple iPhone 11 128 ГБ зеленый",
	"productLink": "http://www.google.com/shopping/product/13471355041199662593?q=iPhone&prds=eto:15160220206529252306_0,pid:1853419364265332599,rsk:PC_8023149794696260886&sa=X&ved=0ahUKEwiYuf7SkMf8AhXdCBAIHV31C7cQ8gIIxAw",
	"price": "RUB 30,970.00",
	"description": "Smartphone · Dual SIM · 4G · Wireless Charging · Dual Lens · GSM Network · CDMA Network · iOS · Facial Recognition · 1792x828",
	"merchantName": "iStoreApple",
	"merchantLink": "http://www.google.com/url?url=https://istoreapple.ru/apple-iphone-11-128-gb-zelenij&rct=j&q=&esrc=s&sa=U&ved=0ahUKEwiYuf7SkMf8AhXdCBAIHV31C7cQguUECNMM&usg=AOvVaw1lIo3tGOvmhqIRKqoHxS3k",
	"shoppingId": "13471355041199662593",
	"reviewsScore": "4.6",
	"reviewsCount": "45,423",
	"positionOnSearchPage": 2,
	"productDetails": "Версия ОС на начало продаж iOS 13 Конструкция водозащита Размеры (ШxВxТ) 75.7x150.9x8.3 мм Процессор Apple A13 Bionic Размер ..."
}
```
