# Payabli Go Library

[![fern shield](https://img.shields.io/badge/%F0%9F%8C%BF-Built%20with%20Fern-brightgreen)](https://buildwithfern.com?utm_source=github&utm_medium=github&utm_campaign=readme&utm_source=https%3A%2F%2Fgithub.com%2Fpayabli%2Fsdk-go)

The Payabli Go library provides convenient access to the Payabli APIs from Go.

## Table of Contents

- [Passing Query Parameters](#passing-query-parameters)
- [Usage](#usage)
- [Environments](#environments)
- [Errors](#errors)
- [Request Options](#request-options)
- [Advanced](#advanced)
  - [Response Headers](#response-headers)
  - [Retries](#retries)
  - [Timeouts](#timeouts)
  - [Explicit Null](#explicit-null)
- [Contributing](#contributing)
- [Documentation](#documentation)
- [Reference](#reference)

## Passing Query Parameters

```go
client := client.NewClient(option.WithApiKey("API_KEY"))

query_parameters := url.Values{}
query_parameters.Add("email(ct)", "test@example.com")

response, err := client.Query.ListCustomers(
  context.Background(),
  "ENTRYPOINT",
  &payabli.ListCustomersRequest{},
  option.WithQueryParameters(query_parameters),
)

if err != nil {
  log.Fatalf("Query failed: %v", err)
}

fmt.Printf("Query successful: %+v\n", response)
```


## Usage

Instantiate and use the client with the following:

```go
package example

import (
    client "github.com/payabli/sdk-go/client"
    option "github.com/payabli/sdk-go/option"
    payabli "github.com/payabli/sdk-go"
    context "context"
)

func do() {
    client := client.NewClient(
        option.WithApiKey(
            "<value>",
        ),
    )
    request := &payabli.RequestPayment{
        Body: &payabli.TransRequestBody{
            CustomerData: &payabli.PayorDataRequest{
                CustomerId: payabli.Int64(
                    4440,
                ),
            },
            EntryPoint: payabli.String(
                "f743aed24a",
            ),
            Ipaddress: payabli.String(
                "255.255.255.255",
            ),
            PaymentDetails: &payabli.PaymentDetail{
                ServiceFee: payabli.Float64(
                    0,
                ),
                TotalAmount: 100,
            },
            PaymentMethod: &payabli.PaymentMethod{
                PayMethodCredit: &payabli.PayMethodCredit{
                    Cardcvv: payabli.String(
                        "999",
                    ),
                    Cardexp: "02/27",
                    CardHolder: payabli.String(
                        "John Cassian",
                    ),
                    Cardnumber: "4111111111111111",
                    Cardzip: payabli.String(
                        "12345",
                    ),
                    Initiator: payabli.String(
                        "payor",
                    ),
                },
            },
        },
    }
    client.MoneyIn.Getpaid(
        context.TODO(),
        request,
    )
}
```

## Environments

You can choose between different environments by using the `option.WithBaseURL` option. You can configure any arbitrary base
URL, which is particularly useful in test environments.

```go
client := client.NewClient(
    option.WithBaseURL(payabli.Environments.Sandbox),
)
```

## Errors

Structured error types are returned from API calls that return non-success status codes. These errors are compatible
with the `errors.Is` and `errors.As` APIs, so you can access the error like so:

```go
response, err := client.MoneyIn.Getpaid(...)
if err != nil {
    var apiError *core.APIError
    if errors.As(err, apiError) {
        // Do something with the API error ...
    }
    return err
}
```

## Request Options

A variety of request options are included to adapt the behavior of the library, which includes configuring
authorization tokens, or providing your own instrumented `*http.Client`.

These request options can either be
specified on the client so that they're applied on every request, or for an individual request, like so:

> Providing your own `*http.Client` is recommended. Otherwise, the `http.DefaultClient` will be used,
> and your client will wait indefinitely for a response (unless the per-request, context-based timeout
> is used).

```go
// Specify default options applied on every request.
client := client.NewClient(
    option.WithToken("<YOUR_API_KEY>"),
    option.WithHTTPClient(
        &http.Client{
            Timeout: 5 * time.Second,
        },
    ),
)

// Specify options for an individual request.
response, err := client.MoneyIn.Getpaid(
    ...,
    option.WithToken("<YOUR_API_KEY>"),
)
```

## Advanced

### Response Headers

You can access the raw HTTP response data by using the `WithRawResponse` field on the client. This is useful
when you need to examine the response headers received from the API call. (When the endpoint is paginated,
the raw HTTP response data will be included automatically in the Page response object.)

```go
response, err := client.MoneyIn.WithRawResponse.Getpaid(...)
if err != nil {
    return err
}
fmt.Printf("Got response headers: %v", response.Header)
fmt.Printf("Got status code: %d", response.StatusCode)
```

### Retries

The SDK is instrumented with automatic retries with exponential backoff. A request will be retried as long
as the request is deemed retryable and the number of retry attempts has not grown larger than the configured
retry limit (default: 2).

A request is deemed retryable when any of the following HTTP status codes is returned:

- [408](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/408) (Timeout)
- [429](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/429) (Too Many Requests)
- [5XX](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/500) (Internal Server Errors)

If the `Retry-After` header is present in the response, the SDK will prioritize respecting its value exactly
over the default exponential backoff.

Use the `option.WithMaxAttempts` option to configure this behavior for the entire client or an individual request:

```go
client := client.NewClient(
    option.WithMaxAttempts(1),
)

response, err := client.MoneyIn.Getpaid(
    ...,
    option.WithMaxAttempts(1),
)
```

### Timeouts

Setting a timeout for each individual request is as simple as using the standard context library. Setting a one second timeout for an individual API call looks like the following:

```go
ctx, cancel := context.WithTimeout(ctx, time.Second)
defer cancel()

response, err := client.MoneyIn.Getpaid(ctx, ...)
```

### Explicit Null

If you want to send the explicit `null` JSON value through an optional parameter, you can use the setters\
that come with every object. Calling a setter method for a property will flip a bit in the `explicitFields`
bitfield for that setter's object; during serialization, any property with a flipped bit will have its
omittable status stripped, so zero or `nil` values will be sent explicitly rather than omitted altogether:

```go
type ExampleRequest struct {
    // An optional string parameter.
    Name *string `json:"name,omitempty" url:"-"`

    // Private bitmask of fields set to an explicit value and therefore not to be omitted
    explicitFields *big.Int `json:"-" url:"-"`
}

request := &ExampleRequest{}
request.SetName(nil)

response, err := client.MoneyIn.Getpaid(ctx, request, ...)
```

## Contributing

While we value open-source contributions to this SDK, this library is generated programmatically.
Additions made directly to this library would have to be moved over to our generation code,
otherwise they would be overwritten upon the next generated release. Feel free to open a PR as
a proof of concept, but know that we will not be able to merge it as-is. We suggest opening
an issue first to discuss with us!

On the other hand, contributions to the README are always very welcome!
## Documentation

API reference documentation is available [here](https://docs.payabli.com).

## Reference

A full reference for this library is available [here](https://github.com/payabli/sdk-go/blob/HEAD/./reference.md).
