## User-defined Transformations for RudderStack

RudderStack gives you the ability to code your own custom transformation functions to implement use-cases based on your requirements. As these transformation functions are written in JavaScript, it is very easy for you to integrate these functions into the RudderStack data pipeline.

This repository contains some useful transformation templates that you can use to create your own user-defined functions.

### How user-defined transformation functions work

The user-defined transformation function:
- Accepts a JSON payload - which is essentially an array of event objects - formatted as per the canonical object model supported by RudderStack
- Performs the user-defined function such as event removal/sampling, value substitution or aggregation on the input array
- Emits the modified payload

## Get Started
The sample user transformations included in this repository can be added via the RudderStack Configuration Plane. To know how to do this in more detail, please check out our [documentation](https://docs.rudderstack.com/).

Here’s a quick visual tutorial on how to do so:

![Demo for User-defined Functions](UDF.gif)

The following sections give you a detailed overview of the functionality of the sample transformation functions:

### User Transformation for PII Detection and Masking
This transformation function takes developer-supplied attribute names along with the values of matching attributes, and replaces them with **X**s or a masked representation, as per the developer's choice.

[Read more](https://rudderstack.com/blog/protect-personally-identifiable-information-pii-using-rudderstack/) on how you can implement this function for your apps.

### User Transformation for Selective Event Removal and Value Aggregation
If an enterprise generates a large volume of events, but the target analytics destination charges by volume - then only certain samples of event data can be sent to the destination for analytics.
This transformation function allows you to:
- Selectively removes events based on a name match
- Selectively removes events based on the value of a given attribute
- Aggregates values of certain attributes for multiple instances of a specific type of event in a batch and then replaces those instances with a single instance containing the aggregated attributes

### User Transformation for Missing Value Substitution and Batch Size Reduction or Sampling
This user transformation does the following:
- Replaces missing values for a User-Agent attribute
- In cases where the developer has populated crucial attributes within nested structures but not at the root level, copies the values to the root level
- Reduces batch size and then selects only a subset of events

### User Transformation for Removing Attributes without Values
In this transformation function, all the attributes within a given event payload which do not have any value are removed to reduce the payload size and optimize the storage space for warehouses.

Please feel free to use these functions and tweak them as per your requirements.

## License
The RudderStack Server is released under the [AGPLv3 license](https://www.gnu.org/licenses/agpl-3.0-standalone.html).

## What is RudderStack
RudderStack is an open-source customer data infrastructure platform for collecting, storing and routing customer event data to the destinations as specified by you. RudderStack runs on your cloud environment or even your data center and provides a powerful framework to process and route your event data on the fly.

RudderStack runs as a single Go binary, with PostgreSQL being the only external dependency. 

To know more about RudderStack, please visit our [website](https://rudderstack.com/) or our [GitHub](https://github.com/rudderlabs) repository. You can also [contact us](https://rudderstack.com/contact/) or join our [Discord](https://discordapp.com/invite/xNEdEGw) channel to know more about the platform, and what we do. Make sure you also check out the [HackerNews discussion](https://news.ycombinator.com/item?id=21081756) around RudderStack!

## Contribute
Please see the [contributing guide](https://github.com/rudderlabs/rudder-server/blob/master/CONTRIBUTING.md) to get more information on how you can contribute to this project. If you have any ideas on developing your own custom transformation functions and want some more inputs or thoughts on them, you can talk to us on our [Discord](https://discordapp.com/invite/xNEdEGw) channel.

## Wiki
- [RudderStack Documentation](https://docs.rudderstack.com/)
- [Destination Transformation in RudderStack](https://docs.rudderstack.com/contributor-guide/create-a-new-destination-transformer-for-rudder)
- [Protect Personally Identifiable Information (PII) in Your Apps Using RudderStack](https://rudderstack.com/blog/protect-personally-identifiable-information-pii-using-rudderstack/)
- [Best Practices for Coding RudderStack Transformation Functions](https://docs.rudderstack.com/contributor-guide/create-a-new-destination-transformer-for-rudder/best-practices-for-coding-transformation-functions-in-javascript#best-practices-for-coding-rudderstack-transformation-functions)
