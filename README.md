[https://apify.com/epctex/duckduckgo-scraper](https://apify.com/epctex/duckduckgo-scraper?fpr=yhdrb)

# Actor - DuckDuckGo Scraper

## DuckDuckGo scraper

Since DuckDuckGo doesn't provide a good and free API, this actor should help you to retrieve data from it.

The DuckDuckGo data scraper supports the following features:

-   Search any keyword - You can search any keyword you would like to have and get the results right away!

-   Search for images, videos, news, or default modes - Search for anything. Not just the default search mode but also for images, videos, and news.

-   Get results by region - Depending on your needs, you can change the settings and retrieve the results by specific regions.

-   Adjust safety modes - Change the safety modes on DuckDuckGo. Turn it on, or off, and make it run in moderate or strict modes.

## Bugs, fixes, updates, and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/duckduckgo-scraper/issues).

## Input Parameters

The input of this scraper should be JSON containing the list of pages on DuckDuckGo that should be visited. Possible fields are:

- `search`: (Required) (String) Keyword that you want to search on DuckDuckGo.

- `searchMode`: (Required) (String) Which mode do you want to start the DuckDuckGo scraper. `images`, `news`, `videos`, and `default` are the possible values that can be provided.

- `region`: (Required) (String) Regions you want to use the DuckDuckGo search engine. To retrieve the results from all regions, it should be `wt-wt`.

- `safeSearch`: (Required) (String) Which safety mode do you want to initiate the DuckDuckGo search? The possible values are `OFF`, `MODERATE`, or `STRICT`.

- `endPage`: (Optional) (Number) Final number of page that you want to scrape. The default is `Infinite`. This applies to all `search` requests and `startUrls` individually.

- `maxItems`: (Optional) (Number) You can limit scraped items. This should be useful when you search through the big lists or search results.

- `proxy`: (Required) (Proxy Object) Proxy configuration.

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).


### Compute Unit Consumption

The actor is optimized to run blazing fast and scrape as many items as possible. Therefore, it forefronts all search requests. If the actor doesn't block very often it'll scrape 100 listings in 10 seconds with ~0.001-0.002 compute units.

### DuckDuckGo Scraper Input example

```json
{
  "search": "vodafone",
  "searchMode": "news",
  "region": "uk-en",
  "safeSearch": "OFF",
  "proxy": {
    "useApifyProxy":true
  }
}
```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with a failure state and output an explanation of what is wrong.

## DuckDuckGo Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any language (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this DuckDuckGo actor.

## Scraped DuckDuckGo Properties

The structure of each item in DuckDuckGo looks like this:

### Search Result

```json
{
    "title": "My Vodafone account | view your bill, offers and settings",
    "description": "My <b>Vodafone</b> log in Quickly update and manage your online account through your My <b>Vodafone</b> account. Check your bill and data usage, make a payment, top up your Pay as you go plan, and more. Take me to log in Upgrade Upgrade your existing plan, find great deals on the latest phones and see how much you could save with a flexible SIM only plan.",
    "rawDescription": "My <b>Vodafone</b> log in Quickly update and manage your online account through your My <b>Vodafone</b> account. Check your bill and data usage, make a payment, top up your Pay as you go plan, and more. Take me to log in Upgrade Upgrade your existing plan, find great deals on the latest phones and see how much you could save with a flexible SIM only plan.",
    "hostname": "www.vodafone.co.uk",
    "icon": "https://external-content.duckduckgo.com/ip3/www.vodafone.co.uk.ico",
    "url": "https://www.vodafone.co.uk/login"
}
```

### Image Result

```json
{
    "height": 538,
    "image": "https://d2t2wfirfyzjhs.cloudfront.net/images/ex-desc/vodafone-business-logo.jpg",
    "image_token": "487e0ca4fc92f9674e6458291c1afa9b8c6fa57aa47b3e22e6f800de0c2c3b08",
    "source": "Bing",
    "thumbnail": "https://tse4.mm.bing.net/th?id=OIP.-0ADG3aYoGKCbuxS8R6WsAHaD5&pid=Api",
    "thumbnail_token": "f6a4af1fca73884f37c9e027093ba41ae0fd732761d003f94aa7dad8ee9e804d",
    "title": "Vodafone Business Broadband Cashback Offers, Discounts & Deals for ...",
    "url": "https://www.topcashback.co.uk/vodafone-business-broadband/",
    "width": 1024
}
```

### Video Result

```json
{
    "url": "https://www.youtube.com/watch?v=bvB0ulL83e4",
    "title": "Vodafone Idea Troubles Mount As Vendors Consider Asking For Advance Payments | Trading Hour",
    "description": "Vendors are likely to consider seeking advance payments from Vodafone-Idea for Jan 2023 onwards. Sources told CNBC-TV18 that pending dues, payment history by Vodafone-Idea are not inspiring confidence among vendors. Sources added further that Indus Tower board may consider \"drastic measures\" like discontinuing services to Voda Idea in case of ...",
    "image": "https://tse3.mm.bing.net/th?id=OVF.T5ONUyMG3qmy7pVlTY8pXw&pid=Api",
    "duration": "2:46",
    "publishedOn": "YouTube",
    "published": "2023-01-13T06:31:06.0000000",
    "publisher": "CNBC-TV18",
    "viewCount": 722
}
```

### News Result

```json
{
    "date": 1674213240,
    "excerpt": "<b>Vodafone</b> UK network chief Andrea Dona called for more government funding for SA 5G as the operator commenced a trial of the tech.",
    "image": "https://www.mobileworldlive.com/wp-content/uploads/2022/01/20220113_5g_vodafone-e1656497723791.jpg",
    "relativeTime": "9 hours ago",
    "syndicate": "Bing",
    "title": "Vodafone claims UK SA 5G first",
    "url": "https://www.mobileworldlive.com/featured-content/home-banner/vodafone-claims-uk-sa-5g-first/",
    "isOld": false
}
```

## Contact
Please visit us through [epctex.com](https://epctex.com) to see all the products that are available for you. If you are looking for any custom integration or so, please reach out to us through the chat box in [epctex.com](https://epctex.com). In need of support? [devops@epctex.com](mailto:devops@epctex.com) is at your service.
