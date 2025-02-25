# Lefties Data API Documentation

## Introduction

Welcome to the Lefties Data API! This comprehensive API provides access to Lefties fashion data, including products, categories, stores, and more. Whether you're building a shopping app, creating a fashion recommendation system, or just exploring what Lefties has to offer, this API makes it easy to access and utilize their data.

This documentation is designed specifically for beginners, with clear explanations and examples to help you get started quickly.

## Why Use the Lefties Data API?

The Lefties Data API offers numerous benefits for developers:

- **Complete Product Information**: Access detailed product descriptions, images, pricing, and availability
- **Search Functionality**: Find products using keywords or browse by categories
- **International Support**: Get data for different countries and in various languages
- **Store Locator**: Find physical stores by country or proximity to a location
- **Product Recommendations**: Discover similar products to enhance user experience
- **Real-time Availability**: Check product stock information across different stores

This API is particularly valuable for:
- E-commerce platforms wanting to integrate Lefties products
- Fashion recommendation applications
- Price comparison tools
- Store locator services
- Market analysis and trend identification

## Getting Started

To use the Lefties Data API, you'll need to:

1. Sign up for a RapidAPI account
2. Subscribe to the [Lefties Data API](https://rapidapi.com/belchiorarkad-FqvHs2EDOtP/api/lefties-data-api)
3. Get your API key
4. Make requests using your preferred programming language

## Base URL
- https://lefties-data-api.p.rapidapi.com

## API Endpoints

The API is organized into several categories of endpoints to help you find what you need.

### Product Search

#### Search Products

```
GET /search
```

Search for products using keywords.

**Query Parameters:**
- `query` (required): Search term (default: "roupa")
- `page` (required): Page number (default: "1")
- `perPage` (required): Results per page (default: "20", max: 75)
- `countryCode` (required): Country code (default: "PT")
- `languageCode` (optional): Language code

**Example Request:**
```
GET https://lefties-data-api.p.rapidapi.com/search?query=jeans&page=1&perPage=20&countryCode=ES
```

#### Auto-Complete Search

```
GET /search/autocomplete
```

Get search suggestions as the user types.

**Query Parameters:**
- `query` (required): Partial search term (default: "leggings")
- `countryCode` (required): Country code (default: "PT")

**Example Request:**
```
GET https://lefties-data-api.p.rapidapi.com/search/autocomplete?query=dre&countryCode=PT
```

### Countries and Languages

#### Get Available Countries

```
GET /countries
```

Retrieve all countries where Lefties operates.

**Example Request:**
```
GET /countries
```

#### Get Country Languages

```
GET /countries/languages
```

Get available languages for a specific country.

**Query Parameters:**
- `countryCode` (required): Country code (e.g., "PT")

**Example Request:**
```
GET https://lefties-data-api.p.rapidapi.com/countries/languages?countryCode=ES
```

### Categories

#### Get Product Categories

```
GET /categories
```

Retrieve all product categories.

**Query Parameters:**
- `countryCode` (required): Country code (default: "PT")
- `languageCode` (required): Language code (default: "en")

**Example Request:**
```
GET https://lefties-data-api.p.rapidapi.com/categories?countryCode=PT&languageCode=en
```

### Products

#### Get Product Description

```
GET https://lefties-data-api.p.rapidapi.com/product/description
```

Get detailed information about specific products.

**Query Parameters:**
- `productIds` (required): Comma-separated product IDs (default: "659620179,659620314")
- `countryCode` (required): Country code (default: "PT")
- `languageCode` (optional): Language code

**Example Request:**
```
GET https://lefties-data-api.p.rapidapi.com/product/description?productIds=659620179,659620314&countryCode=PT
```

#### Get Product by URL

```
GET /product/description/byurl
```

Get product information using a product URL.

**Query Parameters:**
- `productUrl` (required): Full URL to the product (default: a sample URL)

**Example Request:**
```
GET https://lefties-data-api.p.rapidapi.com/product/description/byurl?productUrl=https://www.lefties.com/es/mujer/ropa/vestidos/vestido-denim-camisero-ligero-c1030267514p659617227.html
```

#### Get Products by Category

```
GET /product/bycategory
```

Browse products within a specific category.

**Query Parameters:**
- `categoryId` (required): Category ID (default: "1030459893")
- `page` (required): Page number (default: "1")
- `perPage` (required): Results per page (default: "20", max: 75)
- `countryCode` (required): Country code (default: "PT")
- `languageCode` (optional): Language code (default: "en")

**Example Request:**
```
GET https://lefties-data-api.p.rapidapi.com/product/bycategory?categoryId=1030459893&page=1&perPage=20&countryCode=PT
```

#### Check Product Availability

```
GET /product/availability
```

Check stock information for products.

**Query Parameters:**
- `productIds` (required): Comma-separated product IDs (default: "659620179,659620314")
- `countryCode` (required): Country code (default: "PT")
- `languageCode` (optional): Language code

**Example Request:**
```
GET https://lefties-data-api.p.rapidapi.com/product/availability?productIds=659620179,659620314&countryCode=PT
```

#### Get Similar Products

```
GET /product/similar
```

Get product recommendations based on a specific product.

**Query Parameters:**
- `productId` (required): Product ID (default: "659626387")
- `limit` (required): Maximum number of results (default: "54", max: 75)
- `countryCode` (required): Country code (default: "PT")
- `languageCode` (optional): Language code

**Example Request:**
```
GET https://lefties-data-api.p.rapidapi.com/product/similar?productId=659626387&limit=10&countryCode=PT
```

### Stores

#### Get All Stores

```
GET /stores
```

Get a list of all Lefties stores in a country.

**Query Parameters:**
- `countryCode` (required): Country code (default: "ES")

**Example Request:**
```
GET https://lefties-data-api.p.rapidapi.com/stores?countryCode=ES
```

#### Find Stores by Proximity

```
GET /stores/byproximity
```

Find stores near a specific location.

**Query Parameters:**
- `countryCode` (required): Country code (default: "PT")
- `latitude` (required): Latitude coordinate (default: "40.1548235")
- `longitude` (required): Longitude coordinate (default: "-8.4293891")
- `languageCode` (optional): Language code

**Example Request:**
```
GET https://lefties-data-api.p.rapidapi.com/stores/byproximity?countryCode=PT&latitude=40.1548235&longitude=-8.4293891
```

## Error Handling

The API returns standard HTTP status codes:
- `200`: Success
- `400`: Bad Request (missing parameters)
- `404`: Not Found
- `500`: Server Error

Error responses include a message explaining what went wrong:

```json
{
  "error": "Please provide the countryCode",
  "code": "400"
}
```

## Practical Use Cases

### Building a Fashion Finder App

You can use the Search and Categories endpoints to create a searchable catalog of Lefties products. The Auto-Complete endpoint makes the search experience smooth and user-friendly.

```javascript
// Example: Search for women's dresses
fetch('https://lefties-data-api.p.rapidapi.com/search?query=women+dresses&page=1&perPage=20&countryCode=ES')
  .then(response =&gt; response.json())
  .then(data =&gt; displayProducts(data));
```

### Creating a Store Locator

The Stores endpoints allow you to build a store locator that shows users their nearest Lefties stores.

```javascript
// Example: Find stores near user location
navigator.geolocation.getCurrentPosition(position =&gt; {
  const { latitude, longitude } = position.coords;
  fetch(`https://lefties-data-api.p.rapidapi.com/stores/byproximity?countryCode=ES&latitude=${latitude}&longitude=${longitude}`)
    .then(response =&gt; response.json())
    .then(data =&gt; showNearbyStores(data));
});
```

### Product Recommendation Engine

Use the Similar Products endpoint to create a "You might also like" feature in your app.

```javascript
// Example: Show similar products
fetch('https://lefties-data-api.p.rapidapi.com/product/similar?productId=659626387&limit=4&countryCode=PT')
  .then(response =&gt; response.json())
  .then(data =&gt; displaySimilarProducts(data));
```

## Tips for Beginners

1. **Start Small**: Begin with simple endpoints like product search or category listing
2. **Use Default Values**: The API provides sensible defaults for many parameters, making it easier to start
3. **Check Response Structure**: Examine the API responses to understand the data structure
4. **Handle Errors**: Always implement error handling in your code
5. **Respect Limits**: Stay within the rate limits of your API subscription

## Conclusion

The Lefties Data API offers a powerful way to integrate Lefties fashion data into your applications. With comprehensive product information, search capabilities, and store details, you can create rich, fashion-focused experiences for your users.

Whether you're building a shopping companion, a fashion recommendation system, or a retail analytics platform, this API provides the data foundation you need to succeed.

Start exploring the API today and discover the possibilities for your next project!

## Support

If you encounter any issues or have questions about using the API, please contact RapidAPI support, refer to the official documentation or send us email at pintoflowpt@gmail.com.

Happy coding!
