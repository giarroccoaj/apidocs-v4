## Cash Prices
> Example fetching cash price information:

```shell
curl -i -H "Authorization: Bearer $ACCESS_TOKEN" https://platform.pokitdok.com/api/v4/prices/cash?cpt_code=87799&zip_code=32218
```

```python
pd.cash_prices(zip_code='32218', cpt_code='87799')
```

```ruby
pd.cash_prices({ zip_code: '32218', cpt_code: '87799'})
```

```csharp
client.pricesCash(
    new Dictionary<string, string> {
        { "zip_code", "32218" },
        { "cpt_code", "87799" }
});
```

```java
HashMap<String, String> query = new HashMap<String, String>();
query.put("zip_code", "32218");
query.put("cpt_code", "87799");

Map<String, Object> results = pd.cashPrices(query);
```


*Available modes of operation: real-time*

The Cash Prices endpoint allow access to our internal collection of pricing
data. The data comes from actual providers selling actual services. For a
location where a cash price has not been collected, a price is estimated using a
multivariate model.

While the endpoint requires a five-digit zip code, only the first three digits
are significant. This is because the index is only granular to the first three
digits of the zip code, commonly called a "geozip" or a "ZIP Code Prefix". These
three digits refer to the geographical regions surrounding major cities or
metropolitan areas. There are approximately 900 "geozips" in the United States.

| Endpoint     | HTTP Method | Description                                                                                 |
|:-------------|:------------|:--------------------------------------------------------------------------------------------|
| /prices/cash | GET         | Return a list of prices for a given procedure (by CPT Code) in a given region (by ZIP Code) |

The /prices/cash endpoint accepts the following parameters:

| Field    | Type     | Description                                |
|:---------|:---------|:-------------------------------------------|
| cpt_code | {string} | The CPT code of the procedure in question  |
| zip_code | {string} | Zip code in which to search for procedures |

The /prices/cash response contains the following fields:

| Field                  | Type      | Description                                                               |
|:-----------------------|:----------|:--------------------------------------------------------------------------|
| average_price          | {decimal} | The average cash price for the procedure                                  |
| cpt_code               | {string}  | The CPT code of the procedure                                             |
| pokitdok_procedure_urn | {string}  | A URN that uniquely identifies the procedure                              |
| procedure_description  | {string}  | The description of the procedure                                          |
| geo_zip_area           | {string}  | The three character zip code tabulation area code                         |
| high_price             | {decimal} | The maximum price for the procedure                                       |
| low_price              | {decimal} | The lowest price for the procedure                                        |
| median_price           | {decimal} | The median price for the procedure                                        |
| standard_deviation     | {decimal} | The standard deviation, or variation measure, of prices for the procedure |
