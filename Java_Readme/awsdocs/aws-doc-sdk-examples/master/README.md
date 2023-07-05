[![Build Status](https://github.com/aws/aws-sdk-ruby/workflows/CI/badge.svg)](https://github.com/awsdocs/aws-doc-sdk-examples/actions)
[![GitHub Super-Linter](https://github.com/awsdocs/aws-doc-sdk-examples/actions/workflows/super-linter.yml/badge.svg)](https://github.com/marketplace/actions/super-linter)
![[]](https://img.shields.io/badge/license-MIT%2FApache--2.0-blue)

# AWS SDK Code Examples

This repository contains code examples that demonstrate how to use the [AWSK SDKs](https://aws.amazon.com/developer/tools/) to interact with [AWS services](https://aws.amazon.com/products).

Many examples are injected into the [AWS Documentation](https://docs.aws.amazon.com).

## How this repository is organized

Code examples for each language's SDK can be found within the following subdirectories. The examples here demonstrate the most common uses of the SDK for each language.

| SDK        | folder                                | SDK version | SDK status                                                         |
| ---------- | ------------------------------------- | ----------- | ------------------------------------------------------------------ |
| .NET       | [dotnetv3/](dotnetv3)                 | 3.5+        | ![[]](https://img.shields.io/badge/-GA-blue)                       |
| .NET       | [dotnet/](dotnet)                     | <3.5        | ![[]](https://img.shields.io/badge/-deprecated-red)                |
| C++        | [cpp/](cpp)                           | 1           | ![[]](https://img.shields.io/badge/-GA-blue)                       |
| Go         | [gov2/](gov2)                         | 2           | ![[]](https://img.shields.io/badge/-GA-blue)                       |
| Go         | [go/](go)                             | 1           | ![[]](https://img.shields.io/badge/-deprecated-red)                |
| Java       | [javav2/](javav2)                     | 2           | ![[]](https://img.shields.io/badge/-GA-blue) (Recommended version) |
| Java       | [java/](java)                         | 1           | ![[]](https://img.shields.io/badge/-GA-blue) (Not Recommended)     |
| JavaScript | [javascriptv3/](javascriptv3)         | 3           | ![[]](https://img.shields.io/badge/-GA-blue)                       |
| JavaScript | [javascript/](javascript)             | 2           | ![[]](https://img.shields.io/badge/-GA-blue) (Not Recommended)     |
| Kotlin     | [kotlin/](kotlin)                     |             | ![[]](https://img.shields.io/badge/-preview-brightgreen)           |
| PHP        | [php/](php)                           | 3           | ![[]](https://img.shields.io/badge/-GA-blue)                       |
| Python     | [python/](python)                     | 3           | ![[]](https://img.shields.io/badge/-GA-blue)                       |
| Ruby       | [ruby/](ruby)                         | 3           | ![[]](https://img.shields.io/badge/-GA-blue)                       |
| Rust       | [rust_dev_preview/](rust_dev_preview) |             | ![[]](https://img.shields.io/badge/-preview-brightgreen)           |
| Swift      | [swift/](swift)                       |             | ![[]](https://img.shields.io/badge/-preview-brightgreen)           |

Within each directory, you will find SDK-specific instructions for understanding and invoking example code.

### Additional directories

| directory                     | purpose                                                                                                                                                     | usage                                                                                                                                                                                  |
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/applications](applications) | Contains the non-language-specific components of example applications, which show how the SDKs can be used in the context of a production-like application. | To view the language-specific components for each example application, see the `cross-service` folder in the sub-directory for your desired language (such as `python/cross-service`). |
| [/test](test)                 | Contains all components supporting the custom test automation framework used to routinely test the code in this repository.                                 | Deploys to AWS as a polyglot container-based integration testing solution. WARNING: Still under active construction as of 2023.                                                        |
| [/resources](resources)       | Contains shared components used by many code examples across this repository.                                                                               | Deploys as frontend ([/clients](/resources/clients)) or backend ([/cdk](/resources/cdk) or [/cfn](/resources/cfn)) components.                                                         


## Invoke example code

To invoke this example code, you must have an AWS account. For more information about creating an account, see [AWS Free Tier](https://aws.amazon.com/free/).

You must also have AWS credentials configured. For steps on using the AWS Command Line Interface (AWS CLI) to configure credentials, see [CLI Configuration basics](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html)

## ⚠️ Usage disclaimer

These code examples interact with services that may incur charges to your AWS account. For more information, see [AWS Pricing](https://aws.amazon.com/pricing/).

Additionally, example code might theoretically modify or delete existing AWS resources. As a matter of due diligence, do the following:

- Be aware of the resources that these examples create or delete.
- Be aware of the costs that might be charged to your account as a result.
- Back up your important data.

# Contributing

This repository thrives on your contributions! ❤️ To get involved, see the [CONTRIBUTING.md](CONTRIBUTING.md). 🙏

# Copyright and license

All content in this repository, unless otherwise stated, is
Copyright © Amazon Web Services, Inc. or its affiliates. All rights reserved.

Except where otherwise noted, all examples in this collection are licensed under the [Apache
license, version 2.0](https://www.apache.org/licenses/LICENSE-2.0) (the "License"). The full
license text is provided in the `LICENSE` file accompanying this repository.
