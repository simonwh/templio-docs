# 6-Rendering

Finally time to render your templates!

It's really quite straight forward. You call our [Render API](https://templio.stoplight.io/docs/templio-docs/reference/Templio-API.v1.yaml/paths/~1render/post) with your data, and we return you the rendered template.

## Specifying content type

We currently support renders in `text/html` and `application/pdf` content types.

For PDF, the content is base64 encoded - and just must therefore decode it on your end before saving it or displaying it to a customer.

There's **2** ways to retrieve the content from the render endpoint:

### 1. Render content returned in JSON body (default)

The render will be returned inside a JSON body, in the `result` property. This is the default, together with a rendering in `text/html` format.

```json
{
  "result": "YOUR RENDERED TEMPLATE HERE"
}
```

You can specify the content type you prefer in the render request:

```json
{
  "data": { ... },
  "type": "text/pdf"
}

```

### 2. Render content returned directly

If you want to have the rendered content returned directly (not in a JSON response), you can specify the content type in the `Accept` request header:

```http
POST: https://api.templioapp.com/render?template={YOUR_TEMPLATE_SLUG}
Accept: text/html
Authorization: Apikey {YOUR_API_KEY}

<html>...</html>
```

```http
POST: https://api.templioapp.com/render?template={YOUR_TEMPLATE_SLUG}
Accept: text/pdf
Authorization: Apikey {YOUR_API_KEY}

BASE64_PDF_CONTENT
```


## Overwriting render configuration

You can overwrite certain configurations in the render request:

* `type` - The rendered content type, see above.
* `language` - Language of the render, if you're using translations.


```json
{
  "data": { ... },
  "type": "text/pdf",
  "language": "de"
}

```