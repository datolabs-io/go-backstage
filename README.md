# go-backstage

[![CI](https://github.com/datolabs-io/go-backstage/actions/workflows/ci.yml/badge.svg)](https://github.com/datolabs-io/go-backstage/actions/workflows/ci.yml)
[![codecov](https://codecov.io/gh/datolabs-io/go-backstage/branch/main/graph/badge.svg?token=4CVNSX7UOZ)](https://codecov.io/gh/datolabs-io/go-backstage)
[![Go Reference](https://pkg.go.dev/badge/github.com/datolabs-io/go-backstage/v3.svg)](https://pkg.go.dev/github.com/datolabs-io/go-backstage/v3)

**go-backstage** is a Go client library for accessing the
[Backstage REST API](https://backstage.io/docs/features/software-catalog/software-catalog-api).

The library provides a convenient and easy-to-use interface to access and manipulate data from the Backstage. This library handles
the low-level details of making HTTP requests and parsing responses, allowing developers to focus on building their application logic.

## Installation

With Go installed, run the following to add the package to your project, along with its dependencies:

```bash
go get github.com/datolabs-io/go-backstage/v3
```

Alternatively, you can add import the package as following and run `go get` to install it:

```go
import "github.com/datolabs-io/go-backstage/v3"
```

## Usage

Add the package to your project as following:

```go
import "github.com/datolabs-io/go-backstage/v3"
```

Once imported, create a new Backstage API client to access different parts of Backstage API:

```go
client, err := backstage.NewClient(baseURL, "default", nil)
```

If you want to use a custom HTTP client (for example, to handle authentication, retries or different timeouts), you can pass it as the
third argument:

```go
httpClient := &http.Client{}
client, err := backstage.NewClient(baseURL, "default", httpClient)
```

The client than can be used to access different parts of the API, e.g. get the list of entities, sorted in specific order:

```go
entities, response, err := c.Catalog.Entities.s.List(context.Background(), &ListEntityOptions{
        Filters: []string{},
        Fields:  []string{},
        Order:   []ListEntityOrder{{ Direction: OrderDescending, Field: "metadata.name" },
    },
})
```

Refer to [examples](./examples) directory for more examples.

## Contributing

Contributions to the project are welcome. If you are interested in making a contribution, please review open issues or open a new issue to
propose a new feature or bug fix. Please ensure to follow the code of conduct. Any contributions that align with the project goals and
vision are appreciated. Thank you for your interest in improving the project.

## License

This library is distributed under the Apache 2.0 license found in the [LICENSE](./LICENSE) file.
