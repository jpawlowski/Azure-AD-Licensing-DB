**Table of contents**

* [Introduction and motivation](#introduction-and-motivation)
* [Used terms](#used-terms)
    * [Product](#product)
    * [Service](#service)
    * [Service variant](#service-variant)
    * [Service feature](#service-feature)
    * [Package](#package)
    * [Product license](#product-license)
    * [Service plan](#service-plan)
* [Graphical explanation](#graphical-explanation)
    * [Non-technical diagram](#non-technical-diagram)
    * [Technical diagram](#technical-diagram)
* [File structure](#file-structure)
    * [1. Declarative layer](#1-declarative-layer)
    * [2. Stock layer](#2-stock-layer)
    * [3. Service layer](#3-service-layer)
* [Credits](#credits)
* [Contribute](#contribute)

# Introduction and motivation

This repository contains textual files describing Microsoft online licenses and their containing products and services.

The goal is to have a mostly complete database that is human readable and give a complete picture of all the possibilities and relations.
These files can be used as static input files for programming to help to determine the best combination of product licenses.

# Used terms

There is a lot of confusion about the terms used around Microsoft online licenses. Some of them are technical terms, some of them are non-technical. Some of those are interchangeable, some are not. Also, they are quite often mixed up and cause a lot of confusion when talking about them with other people.

This README tries to implement a useful pattern of terms and explains their possible aliases you might read elsewhere. It does not necessarily mean that other definitions out there are completely wrong. It is just necessary to clear the base and have a common understanding about the different meanings before explaining the structure of these database files in more detail.

Note that as far as interpretation of existing Microsoft documentation can be done, this is considered to have these terms finally declared here.

## Product

A product defines a Microsoft marketing or brand name for a particular service or a combination of services. It is considered a _non-technical term_.

The definition per se is independent from any feature sets a service may have. That means, when speaking about a product, it is intended to have an understanding that is unrelated to licenses, costs, or availability of a particular feature within the service.

A product is mostly what you can purchase from Microsoft.

In case a product includes a combination of many services, this is also called a _product package_ (see definition of a [package](#package) below).

**Examples:**

_Combination of services:_
- Microsoft 365
- Office 365
- Enterprise Mobility + Security

_Single service:_
- Azure Active Directory
- Exchange Online
- SharePoint Online
- Windows 10

## Service

A service is a logical unit as seen by the (end) user. It is considered a _non-technical term_.

The definition per se is independent from any feature sets or service variants. That means, when speaking about a service, it is intended to have an understanding that is unrelated to licenses, costs, or availability of a particular feature.

The difference between a product and a service is that you can purchase the product, but never the service. That means that there could be more services defined, but they are not available to be purchased individually.

**Examples:**

_Sold separately as a product or as part of a product package_:
- Azure Active Directory
- Exchange Online
- SharePoint Online
- Windows 10

_Not sold separately:_
- Microsoft Bookings
- Microsoft Staff Hub

## Service variant

A variant of a service refers to a particular set of features that is enabled for the user. It is considered a _non-technical term_. However, it is interchangeable with the technical term _service plan_ and its use mostly depends on the audience of people you are talking to.

**Examples:**

- Azure Active Directory Premium P1
- Azure Active Directory Premium P2
- Exchange Online (Plan 1)
- Exchange Online (Plan 2)
- SharePoint Online (Plan 1)
- SharePoint Online (Plan 2)

## Service feature

A service feature refers to a particular functionality within a service. It is considered a _non-technical term_ in the first place, but may also be used when talking tech.

A particular set of features may also be referred to as a _service variant_ (see definition above).

**Examples:**

Features of _Azure Active Directory Premium P2:_
- Azure AD Privileged Identity Management
- Azure AD Identity Protection

Features of _Exchange Online (Plan 2):_
- Mailbox size: 100 GB
- Data-loss prevention

## Package

A package is a technical _and_ also a non-technical term at the same time.

This will allow to have different views from different angles onto the same unit, mostly depending on the audience of people talking about it.

In _non-technical_ terms, a package is meant to be seen as a combination of different products that can be purchased as a bundle in order to receive some financial discounts (also see definition of a [product](#product) above).

In _technical_ terms, a package is mixing different service plans into a single product license that can be assigned to a user. From a technical perspective, this is no different from assigning many product licenses containing single services (ignoring some less important services that are not available for individual purchase).

A package can also be a synonym for a [product license](#product-license) (see below).

**Examples:**

- Microsoft 365 **E3**
- Microsoft 365 **E5**
- Office 365 **E1**
- Office 365 **E3**
- Office 365 **E5**
- Enterprise Mobility + Security **E3**
- Enterprise Mobility + Security **E5**

## Product license

This is the billing level of Microsoft online products and services. It is a collection of service plans (see [below](#service-plan)) that are bundled together in order to sell them as a single product. There could be different varieties of product license plans, offering the same service with a different feature set, or in different combinations.

Product license plans are assigned to users either directly or indirectly, using group-based licensing.

Sometimes, a product license is often also referred to as a _product license plan_ or just _license_. However, it is good to avoid the term _plan_ here and to use _license_ instead because it will otherwise be mixed up with a _service plan_.

Some documentation may also refer to this as a _product name_. _SKU_ (short for _Stock Keeping Unit_) might be another generic analogy here. Also, _USL_ (short for _User Subscription License_) might occasionally appear as a synonym.

**Examples:**

_Single product licenses:_
- Visio Online **(Plan 1)**
- Visio Online **(Plan 2)**
- Project Online **Essentials**
- Project Online **Professional**

_Product package licenses:_
- Microsoft 365 **E3**
- Microsoft 365 **E5**
- Office 365 **E1**
- Office 365 **E3**
- Office 365 **E5**
- Enterprise Mobility + Security **E3**
- Enterprise Mobility + Security **E5**

## Service plan

A service plan is the technical equivalent of a _service variant_ (see [above](#service-variant)).

This is the representation for a set of features that can be enabled/disabled for a user or group within a product license. For most services, this will allow some kind of access control to certain features on licensing level which sometimes may be in addition to access control on service level (e.g. when a service allows restricting access to certain users or security groups).

In rare cases, disabling a service plan will be of no effect because included features can only be enabled on tenant level (also see [Microsoft 365 tenant-level services licensing guidance](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-tenantlevel-services-licensing-guidance)). For those services, a service plan is only representing proper licensing for the user. The enablement status is irrelevant for the compliance status of a user as long as the containing product license is assigned to the user.

**Examples:**

Service plans of _Azure Active Directory Premium P1:_
- Azure Active Directory Premium P1
- Cloud App Security Discovery
- Microsoft Azure Multi-Factor Authentication

Service plans of _Azure Active Directory Premium P2:_
- Azure Active Directory Premium P1
- Azure Active Directory Premium P2
- Cloud App Security Discovery
- Microsoft Azure Multi-Factor Authentication

# Graphical explanation

## Non-technical diagram

The following flow diagram shall explain the relationships between the defined terms above in a non-technical manner:

`````
+-------+                           +--------+                   +----------------+                        +--------+
|Product|  consists of one or many  |Services|  has one or many  |Service variants|  provides one or many  |Features|
+-------+ +-----------------------> +--------+ +---------------> +----------------+ +--------------------> +--------+
`````

`````
+-------+                    +--------+                   +----------------+                        +--------+
|Package|  consists of many  |Services|  has one or many  |Service variants|  provides one or many  |Features|
+-------+ +----------------> +--------+ +---------------> +----------------+ +--------------------> +--------+
`````

## Technical diagram

The following flow diagram shall explain the relationships between the defined terms above in a more technical manner, but still on a higher level:

`````
+-------+                                 +----------------+                           +-------------+                        +--------+
|Product|  is represented by one or many  |Product licenses|  consists of one or many  |Service plans|  contains one or many  |Features|
+-------+ +-----------------------------> +----------------+ +-----------------------> +-------------+ +--------------------> +--------+
`````

`````
+-------+                                 +----------------+                           +-------------+                        +--------+
|Package|  is represented by one or many  |Product licenses|  consists of one or many  |Service plans|  contains one or many  |Features|
+-------+ +-----------------------------> +----------------+ +-----------------------> +-------------+ +--------------------> +--------+
`````

# File structure

So, let's bring all defined terms and available info into a technical file structure.

Currently, five database files in JSON format represent the different layers to describe Microsoft products, licenses, their assigned services, and containing features.

`````
      DECLARATIVE                 STOCK                             SERVICE
         LAYER                    LAYER                              LAYER
+-------------------+     +-------------------+     +----------------+----------------------+
| PackagesDb        |     |                   |     |                |                      |
|                   +---> | ProductLicensesDb +---> | ServicePlansDb +--> ServiceFeaturesDb |
| ProductsDb        |     |                   |     |                |                      |
+-------------------+     +-------------------+     +----------------+----------------------+
`````

The attribute `StringId` is used as an anchor (primary key, if you think in SQL structure) to connect the dots between three different layers.
Some attribute values are supposed to be static and cannot be changed per definition:

1. Microsoft static definitions
    - `Guid`
    - `StringId`
2. Self-declared static definitions
    - `Shortname` (as change might result in changed behavior when used in licensing automations, e.g. within group names)

## 1. Declarative layer

This is how Microsoft advertises their online services as products. It is an abstraction from the stock keeping layer to combine different variants of the same product into a single entity.
A single entity will help to (programmatically) compare different variants with each other and handle conflicts between them. On this layer, a conflict is mostly caused by logic, i.e. it shall be avoided to over-license a user for cost efficiency.

There is currently two ways that Microsoft will sell their products to you:

1. As a package / bundle of multiple services (for example, _Microsoft 365_, _Office 365_, _Enterprise Mobility + Security_)
2. As a single product/service (for example, _Azure Active Directory Premium_, _Exchange Online_, _SharePoint Online_)

While both files `PackagesDb` and `ProductsDb` will serve a similar purpose, the actual combination of product licenses they include are totally different. While `PackagesDb` represents bundles that Microsoft offers to you for saving money when you want to use multiple services at once, the `ProductsDb` will basically represent a single entity for each service that Microsoft has in their portfolio and that you can purchase separately.

## 2. Stock layer

Generally spoken, this "flattens" the 1st layer and is the unit that you can actually purchase from Microsoft (= Stock Keeping Unit, short _SKU_).
A product defines a combination of one or more meaningful service plans. When a combination contains service plans from multiple different services, this is considered a _package_ or _bundle_. If a combination only contains service plans from a single service, this is considered a _single product license_.
There can be different variants and combinations addressing the same service, but with different feature sets enabled for the user.

Please note that not every SKU can be purchased by everybody. Most often, availability of an SKU depends on your institutional status (e.g. corporation, education, or public sector). Procurement and ways of distribution is not a big topic here as this is mainly about receiving different prizes for the same SKU and may be up to your volume of licenses and your negotiation capabilities.

Technically, items in the file `ProductLicensesDb` do simply represent a combination of service plans from layer 3.

## 3. Service layer

The service layer is the most interesting one as this highly affects what features a user may use within a service. Therefore, this is the most important part when licensing a user for Microsoft online services as it will have immediate impact on your end-user experience.

Usually, this is the layer where you would start planning what you want your users to be able to use. Every item in `ServicePlansDb` represents a feature set of a Microsoft online service that you can choose from. Once you have made your choices, the attribute `ProductLicenses` will give you a first indicator about your options to purchase this particular set of features for the respective service.

This layer consists of two parts:

### Part 1: Service plan

Access to a single Microsoft online service is given to the user by enabling a service plan for it.

The service plan also describes what kind of features this user will be able to use within the service. However, those features are predefined by Microsoft and therefore can not be changed. This is why the service layer mainly consists of the service plans. However, during license procurement it is often required to know how a specific feature that any of the stakeholders has requested can be purchased. See [part 2](#part-2-service-features) below for further explanation.

Depending on the actual service, there can be excluding service plans that you cannot enable for a single user at the same time. This is because otherwise their different feature sets will interfere with each other. Some services might handle this gently and will automatically detect the highest feature set that ultimately should be enabled for the user (e.g. Azure Active Directory). However, most of the services don't and probably never will due the historical architecture of that service. Microsoft APIs will usually not let you enable conflicting service plans at the same time.
Note that this kind of conflicts are defined on the declarative layer 1, although they seem to become relevant only on this 3rd layer.
On the other hand, there can also be additive service plans which will enable more features for the user. Usually this causes a dependency to have another service plan for that particular service enabled first. This is what is described directly within the `ServicePlansDb` file using the attribute `RequiredServicePlans`.

### Part 2: Service features

It is often hard to identify which particular features of a service are included in which available service plans and therefore which product licenses could be considered to make a specific feature available to users.

Also, there can be confusion about features because they are sometimes identified as a service by their own or mixed up being a separate product. Microsoft marketing talk is of no help here and even makes it more complicated and confusing.

The file `ServiceFeaturesDb` is supposed to help with this and has a one-to-many relation to items in file `ServicePlansDb`.

# Credits

There are a couple of people who either directly or indirectly participarted to define the files in this repository.

In alphabetic order:

- Sebastian Bauer ([AgilSchmiede](https://agilschmiede.de/)): Used language to define terms; overall sense of purpose
- Simon Brunner ([digatus](https://www.digatus.de/)): Programmatic capability cross-check
- Mathias Müller ([digatus](https://www.digatus.de/)): Data validation
- [Julian Pawlowski](https://julian.pawlowski.me/en/) ([digatus](https://www.digatus.de/)): Initial data collection, structuring, and validation; current maintainer and architect

Besides those persons pointed out here, there may be other contributors which can be found on [Github](https://github.com/jpawlowski/Azure-AD-Licensing-DB/graphs/contributors).

# Contribute

**This set of files is in the early stages and should be considered _under construction_ until further notice.**

## Issues

If you discover any issues, please feel free to open a [ticket](https://github.com/jpawlowski/Azure-AD-Licensing-DB/issues) for it on Github. Your participation will be _highly_ appreciated.
Opening a [pull request](https://github.com/jpawlowski/Azure-AD-Licensing-DB/pulls) for something that shall be corrected is even more welcome ;-) .

## Missing product licenses and service plans

Also, there for sure are a lot of product licenses and service plans missing from the index, and they all shall be added over time. If you are aware of any other product licenses and/or service plans, opening a pull request to put them into the correct files would be great.

Please make sure to always include these attributes:

1. `Guid` - Unique identifier as defined by Microsoft
2. `StringId` - Static textual identifier alias as defined by Microsoft
3. `Name` - Current display name used in Microsoft Azure Portal
4. `Aliases` - Any known aliases for the display name that might have been used in the past, e.g. before a product or service was renamed or rebranded
5. `DistributionStatus` - In case of a product license, is it still available for sale?

## Missing details about features of a service plan

Do you know more about features that are included into a particular service plan? That's great! I encourage you to open a [ticket](https://github.com/jpawlowski/Azure-AD-Licensing-DB/issues) to have this added to the `ServiceFeaturesDb` file or even create a [pull request](https://github.com/jpawlowski/Azure-AD-Licensing-DB/pulls) by yourself (will automatically give you credits and reputation on Github ;-)).
