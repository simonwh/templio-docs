# Pre-processors

One of the most powerful features are Templio's Javascript pre-processors. A pre-processor is a snippet of Javascript code which receives `input data` and render configuration as input, and returns the same. Within the code, you can modify your data and change the rendering logic. It gives you _a lot_ of power over your templates. 

Pre-processors are great if you need to:

* Use advanced logic that is not easily doable in Liquid
* Transform input data into a different structure
* Fetch additional data from external APIs
* Overwrite render configuration, such as language, based on input data
* Anything else you do with Javascript and your data

Pre-processors can be chained, and will run in the order you specify for each template.

## Creating a pre-processor

Every pre-processor starts with the following code:

```javascript
module.exports = (input) => {
  // Modify input here, make sure to return a data property
  return input;
};
```

You can any write any Javascript code and [use NPM packages](#Using-npm-packages) - as long as you `return input` at the end.

The `input` variable contains the input data (`input.data`) sent to the template (or the result of a previous pre-processor if chained). You can also overwrite certain render configurations, such as language, by setting `input.language`.

If we, for example, send a list of order items with prices in our input data:

```json
{
  "data": {
    "order_items": [{ "name": "Rocket", "price": 1000 }, { "name": "Rocket Fuel", "price": 50}]
  }
}
```

And we wish to sum the prices for a total amount, we easily do it with a pre-processor:

```javascript
module.exports = (input) => {
  
  input.total_amout = input.data.order_items.reduce(function(acc, order_item) { return acc + order_item.price }, 0)

  return input;
};
```

The output of the pre-processor will be:

```json
{
  "data": {
    "order_items": [{ "name": "Rocket", "price": 1000 }, { "name": "Rocket Fuel", "price": 50}],
    "total_amount": 1050
  }
}
```


## How does it work?



## Using npm packages

We currently support the following npm packages:

* `moment`
* `axios`

If you need to use any other packages, please contact us and we add them for you.

You can require and use the packages like this:

```javascript
module.exports = (input) => {
  const axios = require('axios');

  return input;
};
```



Advanced use cases
- Change languages
- Request external data