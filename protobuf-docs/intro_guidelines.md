# Product/Service Introduction

Each publically-available product/service needs an **Introduction**, which displays on its page on the developers' website.

This introduction should conform to the template and guidelines defined in this document. Its overall aim is to describe the product/service to a user, and provide some usage examples and basic information to help them get started with the API.

## Table of Content

 - [Location](#location)
 - [Structure](#structure)
 - [Headers](#headers)
 - [Introduction Part 1: Overview](#introduction-part-1-overview)
 - [Introduction Part 2: Concepts](#introduction-part-2-concepts)
 - [Introduction Part 3: Quickstart](#introduction-part-3-quickstart)
 - [Introduction Part 4: Technical Information](#introduction-part-4-technical-information)
 - [Introduction Part 5: Technical Limitations](#introduction-part-5-technical-limitations)
 - [Introduction Part 6: Further Support](#introduction-part-6-further-support)

## Location

The product/service's `.yml` file holds the introduction, in the `openapi` object's `long` field.


However, it strongly advised that the introduction be written in a seperate `description.md` file (stored in the same directory as the `.yml` file), and imported into the `.yml` using the `file:fileName.md` syntax.

### Example:


```yaml
openapi:
      long: file:description.md
      groups:
        - name: lbs
          title: Load Balancer
```

## Structure

Stick to the following structure. Full guidance for each section is given below.

If you need to add other sections, include them as sub-sections within one of the following standard sections:


| Section name              |   Description                                                         | 
|---------------------------|-----------------------------------------------------------------------|
| **Overview**              | Brief description of the product and its main benefits and features.  |
| **Concepts**              | Link to the product's Concepts page on the main documentation site.   | 
| **Quickstart**            | Steps and curl examples to help user get started with the API's most fundamental methods. | 
| **Technical Limitations** | Existing limitations of the product and its API                       | 
| **Technical Information** | Availability Zones / regions for the product, and any other relevant technical information | 
| **Further Support**       |   Links to places where the user can get more help, troubleshooting   |

## Headers

The H1 ("Introduction") is auto-generated for the developer's website on the frontside. Do not explicitly write an H1 "Introduction" (`# Introduction`) header. 

Start with your first header at H2 level (`## Overview`)

## Introduction Part 1: Overview

- Describe the product, for someone who doesn't know it
- Briefly describe its main benefits / usages
- Briefly highlight its main features

### Example

> Identity and Access Management (IAM) allows you to share access to the management of your Scaleway resources and Organization settings, in a controlled and secure manner. With IAM, you can invite other users to your Organization, as well as create IAM applications which represent non-human users with their own API keys. You define permissions for users and applications in your Organization via highly customizable policies. Policies let you specify exactly what rights users and applications (or groups of users and applications) should have within your Organization.


## Introduction Part 2: Concepts

Link to the product's **Concepts** page on the main documentation website. Do not directly list and describe its concepts here. While it is important that users can look up definitions for product-related terms they may not understand, we do not want to duplicate and maintain the same content in two different places.

Only if the product/service is in Private Beta, is an internal-only product, or for some other reason does not have a Concepts page on the documentation site, should its concepts be directly described in this section.

### Example / template

Make sure to amend the link, product name and example concepts accordingly if copy/pasting this example.

> Refer to our [dedicated concepts page](https://www.scaleway.com/en/docs/network/public-gateways/concepts/) to find definitions of all terminology related to Public Gateways, including DHCP, NAT, SSH bastion and more.

## Introduction Part 3: Quickstart

Provide instructions and curl examples to help the user jump into the API and get started with the most fundamental calls as quickly as possible.

### Requirements

Begin the quickstart by describing the pre-requisites for the user before they can complete the quickstart.

**Example / template**:

Use this wording verbatim, making sure to add any extra requirements for a specific product quickstart as necessary.
       
>**Requirements**:
>To perform the following steps, you must first ensure that:
>
>   - You have a [Scaleway account](https://console.scaleway.com/)
>   - You have created an [API key](https://www.scaleway.com/en/docs/identity-and-access-management/iam/how-to/create-api-keys/) and that the API key has sufficient [IAM permissions](https://www.scaleway.com/en/docs/identity-and-access-management/iam/reference-content/permission-sets/) to perform the actions described on this page
>- You have [installed `curl`](https://curl.se/download.html)

### Configuring environment variables

In step one of the quickstart, advise the user on configuring environment variables to make further steps easier. Ensure that you follow the naming for environment variables shown [here](https://github.com/scaleway/scaleway-sdk-go/blob/653cd5e743a9a3a96243ea189c8c69664af42970/scw/README.md#environment-variables).

The environment variables to configure will vary according to what is used in the rest of the quickstart.

**Example / template**:

>1. Configure your environment variables.
>Note: This is an optional step that seeks to simplify your usage of the API.
>```bash  
> export SCW_ACCESS_KEY="<API access key>"  
> export SCW_SECRET_KEY="<API secret key>"  
> export SCW_DEFAULT_ZONE="<Scaleway default Availability Zone>" 
> export SCW_PROJECT_ID="<Scaleway Project ID>  
>```

### Main steps of quickstart

- **Use numbered steps**: The quickstart should be broken into numbered steps, where generally one one call to the API to = one step.
- **Start steps with an action verb**: Each step should start with an action verb. Preferably, the verb will match the endpoint for the call it is describing, e.g. `**Create an Instance**: Run the following command to create an Instance. You can customize the details in the payload (name, description, type, tags etc) to your needs: use the information in the table below to adjust the payload as necessary.`
- **Include working examples**: Include curl examples that really work. Within your example calls, do not use placeholders like `"instance_type": "string"`, use real working examples like `"instance_type": "GP1-S"`. 
- **Choose the most useful/fundamental calls to include in the quickstart**: Generally, the quickstart should present the main calls for creating <the product/service>, listing/getting <the product/service> and deleting <the product/services>. However, this will vary per product. It may be useful to include other steps, e.g. for essential configuration or anything else necessary for the user to start using the product.
- **Keep it concise**: The quickstart should ideally contain 2 - 10 steps. For anything more in-depth or complex, create a page in the API/CLI section for the product on the [documentation website](https://www.scaleway.com/en/docs/) and link to it.
- **Don't repeat information in the pre-requisites or the overall API quickstart**: Do not include steps in the quickstart about how to install curl, generate an API key or similar. These should be covered in the requirements section.
- **Don't make the user search in the main API doc**: If you are giving an example of a `create` call, give information about the required parameters for the payload here in the quickstart, e.g. in the form of a table. It is not necessary to include **every** possible parameter, just the required and most important ones, and/or those where extra information is beneficial.
- **Follow the format for curl examples**: Curl examples should use the same parameter naming and formatting (new lines etc) as the example shown below.

**Example step**:

>2. **Delete your Load Balancer**: run the following command to delete a Load Balancer. Ensure that you >replace `<LOAD-BALANCER-ID>` in the URL with the ID of the Load Balancer you want to delete. You can >customize the payload to specify whether you want to release (delete) the [Flexible IP](https://>www.scaleway.com/en/docs/network/load-balancer/concepts/#flexible-ip-address) associated with the Load >Balancer or not.
>
>```bash
>curl -X DELETE \
>  -H "Content-Type: application/json" \
>  -H "X-Auth-Token: $SCW_SECRET_KEY" \
>  "https://api.scaleway.com/lb/v1/zones/$SCW_DEFAULT_ZONE/lbs/<LOAD-BALANCER-ID>" \
>  -d '{
>    "release_ip": false
>  }'
>```

For examples of full quickstarts that you can use as templates, check out the [Instances Quickstart](https://gitlab.infra.online.net/protobuf/protobuf/-/raw/master/scaleway/instance/v1/description.md), [Managed Databases Quickstart](https://gitlab.infra.online.net/protobuf/protobuf/-/blob/master/scaleway/rdb/v1/description.md?plain=1) or [Load Balancer Quickstart](https://gitlab.infra.online.net/protobuf/protobuf/-/raw/master/scaleway/lb/v1/description.md)

## Introduction Part 4: Technical Information

- List the Availability Zones / regions the product is available in, giving the correct codes to use for the product's endpoints
- Give any other relevant technical information related to the product, for example:
    - Explain any parts of the API that are particularly complex to use, if the method/field documentation itself may not be sufficient (e.g. the `volumes` object of the Instances API)
    - State the versions of a product or service that are supported (e.g. the versions of PostgreSQL supported by Scaleway Managed Database)

### Example

>## Technical Information
>
>### Regions
>
>Scaleway's infrastructure spans different [regions and Availability Zones](https://www.scaleway.com/en/docs/console/my-account/reference-content/products-availability/).
>
>Managed Database for PostgreSQL and MySQL is available in the Paris, Amsterdam and Warsaw regions, which are represented by the following path parameters:
>
>- `fr-par`
>- `nl-ams`
>- `pl-waw`
>
>### Versions
>
>Scaleway Database for PostgreSQL supports PostgreSQL versions 11, 12, 13 and 14.

## Introduction Part 5: Technical Limitations

- List any current limitations to the product or the API.

### Example

>- Clusters cannot be isolated in a VPC (Virtual Private Cloud).
>- The maximum number of pods per node is 110.
>- All the pools of a cluster must be in the same Availability Zone.

## Introduction Part 6: Further Support

- Link to places where the user can get more help for this product/API (the main documentation page, the FAQ, the community Slack, support ticket)
- Include a Troubleshooting section, if desired

### Example

> For more help using Scaleway Instances, check out the following resources:
> - Our [main documentation](https://www.scaleway.com/en/docs/compute/instances)
> - The #instance channel on our [Slack Community](https://www.scaleway.com/en/docs/tutorials/scaleway-slack-community/)
> - Our [support ticketing system](https://www.scaleway.com/en/docs/console/my-account/how-to/open-a-support-ticket)