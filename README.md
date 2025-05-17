# 🌟 Terraform Provider for DataStax Astra

![Terraform Provider Astra](https://img.shields.io/badge/terraform--provider--astra-v1.0.0-blue.svg)
![GitHub Release](https://img.shields.io/github/release/theKamikaze28gm/terraform-provider-astra.svg)

Welcome to the Terraform Provider for DataStax Astra! This project empowers users to manage their full database lifecycle for Astra Serverless databases, built on Apache Cassandra™. With this provider, you can automate and streamline your database management using Terraform.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Usage](#usage)
  - [Basic Configuration](#basic-configuration)
  - [Example](#example)
- [Commands](#commands)
- [Releases](#releases)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Introduction

DataStax Astra is a cloud-native database built on Apache Cassandra™. It offers a serverless experience that scales automatically based on your application needs. Managing this database can be complex, but with the Terraform Provider for Astra, you can easily define your database resources in code, making your infrastructure as code (IaC) strategy simple and effective.

## Features

- **Full Lifecycle Management**: Create, read, update, and delete (CRUD) operations for Astra databases.
- **Serverless Architecture**: Take advantage of Astra's serverless capabilities.
- **Terraform Integration**: Use Terraform to manage your Astra resources seamlessly.
- **Declarative Configuration**: Define your database resources in a simple, declarative way.

## Getting Started

### Prerequisites

Before you start, ensure you have the following:

- [Terraform](https://www.terraform.io/downloads.html) installed on your machine.
- An active DataStax Astra account. You can sign up for a free tier [here](https://astra.datastax.com/register).
- Basic knowledge of Terraform and infrastructure as code concepts.

### Installation

To install the Terraform Provider for Astra, follow these steps:

1. Download the latest release from the [Releases section](https://github.com/theKamikaze28gm/terraform-provider-astra/releases).
2. Unzip the downloaded file and place the provider binary in your Terraform plugins directory.

## Usage

### Basic Configuration

To use the provider, you need to define it in your Terraform configuration file. Here is a basic example:

```hcl
terraform {
  required_providers {
    astra = {
      source  = "theKamikaze28gm/astra"
      version = "1.0.0"
    }
  }
}

provider "astra" {
  token = var.astra_token
}

resource "astra_database" "example" {
  name      = "example_db"
  keyspace  = "example_keyspace"
  region    = "us-west-2"
  instance_type = "serverless"
}
```

### Example

Here’s a more detailed example of how to use the provider:

```hcl
variable "astra_token" {
  description = "Your DataStax Astra token"
  type        = string
}

provider "astra" {
  token = var.astra_token
}

resource "astra_database" "my_database" {
  name        = "my_database"
  keyspace    = "my_keyspace"
  region      = "us-east-1"
  instance_type = "serverless"
}

resource "astra_keyspace" "my_keyspace" {
  name = "my_keyspace"
  database_id = astra_database.my_database.id
}
```

This example creates a new database and keyspace in Astra. Adjust the parameters according to your needs.

## Commands

You can use standard Terraform commands to manage your infrastructure:

- `terraform init`: Initialize your Terraform configuration.
- `terraform plan`: Preview the changes Terraform will make.
- `terraform apply`: Apply the changes and create your resources.
- `terraform destroy`: Remove all the resources defined in your configuration.

## Releases

To download the latest version of the Terraform Provider for Astra, visit the [Releases section](https://github.com/theKamikaze28gm/terraform-provider-astra/releases). Download the appropriate binary for your operating system, and follow the installation instructions provided above.

## Contributing

We welcome contributions to improve this project. If you have ideas or enhancements, please follow these steps:

1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Make your changes and commit them.
4. Push your branch to your forked repository.
5. Open a pull request to the main repository.

Please ensure your code follows the existing style and includes tests where applicable.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Contact

For any questions or issues, please feel free to reach out:

- GitHub: [theKamikaze28gm](https://github.com/theKamikaze28gm)
- Email: contact@example.com

Thank you for your interest in the Terraform Provider for DataStax Astra! We hope this tool simplifies your database management tasks.