## Show

*Applies to: Products API &#8226; Stores API &#8226; Reviews API &#8226; Categories API*

The Show attribute allows you to control which attributes are returned. You can return specific attributes by following the syntax in **Show Only** description. To return all attributes follow the syntax in the **Show All** description.

### Show Only

*Applies to: Products API &#8226; Stores API &#8226; Reviews API &#8226; Categories API*

If you tried the example query in the Getting Started section, you probably noticed that our Products API returns a lot of attributes for each product. For convenience, we provide a `show` query parameter that allows you to specify just the attributes that you want returned in the response.

For example, if you are only interested in the product's `sku`, `name` and `salePrice`, you can list these attributes in the show parameter.

### Products Response `show=sku,name,salePrice`

```shell
curl "https://api.bestbuy.com/v1/products/8880044.json?show=sku,name,salePrice&apiKey=YourAPIKey"
```

```json-doc
{
  "sku": 8880044,
  "name": "Batman Begins (Blu-ray Disc)",
  "salePrice": 7.99
}
```

<div></div>

### Show All

*Applies to: Products API &#8226; Stores API*

In order to make the API responses more manageable, we don't return all available attributes for those items that contain many (e.g. <Products and Stores). In the event that you want to use one of these hidden attributes, you can set `show=all` in the query parameters for the API

For example, the Stores API does not return the `detailedHours` attribute by default. By setting `show=all` you will receive `detailedHours` in the response. Both the default response and the response containing `detailedHours` are provided below for store 2387.

### Stores Response - Default Attributes Only

```text
https://api.bestbuy.com/v1/stores/2387.json?apiKey=YourAPIKey
```

```json-doc
{
  "storeId": 2387,
  "name": "Best Buy Mobile - Richfield",
  "longName": "Best Buy Mobile - Richfield",
  "address": "6601 Nicollet Ave S",
  "city": "Richfield",
  "region": "MN",
  "fullPostalCode": "55423",
  "country": "US",
  "lat": 44.882942,
  "lng": -93.2775,
  "hours": "Mon: 11-8; Tue: 11-8; Wed: 11-8; Thurs: 11-8; Fri: 11-8; Sat: 11-7; Sun: 11-6",
  "hoursAmPm": "Mon: 11am-8pm; Tue: 11am-8pm; Wed: 11am-8pm; Thurs: 11am-8pm; Fri: 11am-8pm; Sat: 11am-7pm; Sun: 11am-6pm",
  "gmtOffset": -6,
  "services": [
    {
      "service": "Best Buy Mobile Specialty Store"
    },
    {
      "service": "Electronics Recycling"
    },
    {
      "service": "Samsung Experience Shop"
    }
  ],
  "phone": "612-866-0957",
  "postalCode": "55423"
}
```

<div></div>

### Stores Response `show=all`

```text
https://api.bestbuy.com/v1/stores/2387.json?show=all&apiKey=YourAPIKey
```

```json-doc
{
  "storeId": 2387,
  "name": "Best Buy Mobile - Richfield",
  "longName": "Best Buy Mobile - Richfield",
  "address": "6601 Nicollet Ave S",
  "city": "Richfield",
  "region": "MN",
  "fullPostalCode": "55423",
  "country": "US",
  "lat": 44.882942,
  "lng": -93.2775,
  "hours": "Mon: 11-8; Tue: 11-8; Wed: 11-8; Thurs: 11-8; Fri: 11-8; Sat: 11-7; Sun: 11-6",
  "hoursAmPm": "Mon: 11am-8pm; Tue: 11am-8pm; Wed: 11am-8pm; Thurs: 11am-8pm; Fri: 11am-8pm; Sat: 11am-7pm; Sun: 11am-6pm",
  "gmtOffset": -6,
  "services": [
    {
      "service": "Best Buy Mobile Specialty Store"
    },
    {
      "service": "Electronics Recycling"
    },
    {
      "service": "Samsung Experience Shop"
    }
  ],
  "phone": "612-866-0957",
  "postalCode": "55423",
  "detailedHours": [
    {
      "day": "Sunday",
      "date": "2014-04-27",
      "open": "11:00",
      "close": "18:00"
    }
```

Notice that the `detailedHours` are included at the bottom of the response in this example.