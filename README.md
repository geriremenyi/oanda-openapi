# OpenAPI Specification for OANDA's v20 REST API

This repository contains a more organized version of the [generated OANDA v20 REST API's OpenAPI specification](https://github.com/oanda/v20-openapi). The specification is rewritten to leverage OpenAPI's newest (3.x.x) syntax. Specifications are moved to separate files and redundancy is removed.

## Demo

The specification is published using SwaggerUI hosted on this repo's github page:

[https://geriremenyi.github.io/oanda-v20-openapi](https://geriremenyi.github.io/oanda-v20-openapi)

## Getting started

### Prerequisites

- [Node](https://nodejs.org/en/) for dev environment,
- [Yarn](https://classic.yarnpkg.com/en/docs/install) for package dependencies.
- (optional) [Visual Studio Code](https://code.visualstudio.com/) for IDE.

### Local setup

1. Clone this repo

```console
git clone https://github.com/geriremenyi/oanda-v20-openapi.git
```
or
```console
git clone git@github.com:geriremenyi/oanda-v20-openapi.git
```

2. Navigate to the root of the cloned project and install all dependencies
```console
yarn install
```

### Bundle

To combine seperate `.yaml` files into one openapi sperification run the following command:
```console
yarn bundle
```

>While the whole point of the repository is to separate individual models and endpoints into seperate files most of the tools cannot handle relative `$ref` properly. The [code generator tool](https://github.com/OpenAPITools/openapi-generator) breaks from version to version. For more details on the problem see the [code generator bugs](https://github.com/OpenAPITools/openapi-generator/issues?q=is%3Aissue+is%3Aopen+relative+ref+).

### Validate

To validate that the specification complies with the OpenAPI 3 standards run the following commands:

1. Separate files with relative reference resolution
```console
yarn validate:original
```
2. Bundled version
```console
yarn validate:bundled
```

### Generate code

To generate C# (.NET core) client run the following command:
```shell
yarn generate:csharp-netcore
```

You can add more code generators via defining it in the [config](config) folder and creating a new run command in the [package.json](package.json).

## Generated client repos

> TODO rewrite this section

There is a [continuous integration](.github/workflows/continuous_integration.yaml) job setup which [runs on every pull request](https://github.com/geriremenyi/oanda-dotnet-client/actions?query=workflow%3A%22Continuous+Integration%22). This makes sure that the definition is syntactically correct.

There is also a [continuous deployment](.github/workflows/continuous_deployment.yaml) job setup which [runs on every merge to master](https://github.com/geriremenyi/oanda-dotnet-client/actions?query=workflow%3A%22Continuous+Deployment%22). This generates the client codes and pushes them to the corresponding GitHub repos.

### C# (.NET core)

The generated C# code is pushed to [nuget.org](https://www.nuget.org/) on every push to the target client repository.

Repository: https://github.com/geriremenyi/oanda-dotnet-client

Nuget package: https://www.nuget.org/packages/GeriRemenyi.Oanda.V20.Client/

> TODO end

## Contribution

[Read more](CONTRIBUTING.md)

## License

[MIT](LICENSE)