---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-18"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}

# Information security
{: #information-security}

IBM is committed to providing our clients and partners with innovative data privacy, security and governance solutions.
{: shortdesc}

**Notice:**
Clients are responsible for ensuring their own compliance with various laws and regulations, including the European Union General Data Protection Regulation. Clients are solely responsible for obtaining advice of competent legal counsel as to the identification and interpretation of any relevant laws and regulations that may affect the clients’ business and any actions the clients may need to take to comply with such laws and regulations.

The products, services, and other capabilities described herein are not suitable for all client situations and may have restricted availability. IBM does not provide legal, accounting or auditing advice or represent or warrant that its services or products will ensure that clients are in compliance with any law or regulation.
If you need to request GDPR support for {{site.data.keyword.cloud}} {{site.data.keyword.watson}} resources that are created


- In the European Union, see [Requesting support for IBM Cloud Watson resources created in the European Union](/docs/services/watson/getting-started-gdpr-sar.html#request-EU).
- Outside the European Union, see [Requesting support for resources outside the European Union](/docs/services/watson/getting-started-gdpr-sar.html#request-non-EU).

## European Union General Data Protection Regulation (GDPR)
{: #gdpr}

IBM is committed to providing our clients and partners with innovative data privacy, security and governance solutions to assist them on their journey to GDPR compliance.

Learn more about IBM's own GDPR readiness journey and our GDPR capabilities and offerings to support your compliance journey [here ![External link icon](../../icons/launch-glyph.svg "External link icon")](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/gdpr){: new_window}.

## Labeling and deleting data in {{site.data.keyword.visualrecognitionshort}}
{: #gdpr-visrec}

### GDPR Security Migration
{: #gdpr-visrec-update}

- All {{site.data.keyword.visualrecognitionfull}} service instances created before **May 22, 2018** are not suitable for clients that require compliance with the EU General Data Protection Regulation EU 2016/679 (GDPR).

- Clients that are subject to GDPR need to [migrate to a new {{site.data.keyword.visualrecognitionshort}} service instance](/docs/services/visual-recognition/migrate.html#migrating) available on **May 22nd, 2018** and to adopt the new agreement for the {{site.data.keyword.visualrecognitionshort}} service.

- Clients will be required to provision a new {{site.data.keyword.visualrecognitionshort}} service and generate *new authentication keys* to utilize the new {{site.data.keyword.visualrecognitionshort}} service.

- If a client does not provision the new {{site.data.keyword.visualrecognitionshort}} service, you confirm that IBM is not processing any Personal Data on the client's behalf that is subject to the GDPR.

- Clients who do not move to the new {{site.data.keyword.visualrecognitionshort}} service between May 22, 2018 and October 1, 2018 will have their data deleted.

### Labeling data

If you need to remove an individual customer's data from a {{site.data.keyword.visualrecognitionshort}} service instance with multiple customers, you first need to associate that data with a unique **Customer ID** for each individual that might have provided data. To specify the Customer ID for any data sent using the `POST /classifiers` method, include the **X-Watson-Metadata: customer_id** property in your header. The following example associates the customer ID `my_ID` with the data passed with a `POST /v3/classifiers` request:

```bash
curl -X POST \
--header "X-Watson-Metadata: customer_id=my_ID" \
--form "apple_positive_examples=@apples.zip" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers?version=2018-03-19"
```
{: pre}

**Note**: Multi-byte characters are supported for the Customer ID string. Characters must be URL-encoded, both in the header during training, and in the query parameter during deletion. Only `_` is allowed; the list of special characters that are not supported is:

```\ | * { } $ - [ ] / ' ` " ~ ? ; < > ( ) ! & = % # ^ @ : . , + space```

**Note**: You are responsible for creating customer_ID values, and ensuring that each is unique.

### Deleting labeled data

To delete all data that is associated with a customer ID, use the `DELETE /v3/user_data` method. You pass the string `customer_id={id}` as a query parameter with the request. The following example deletes all data for the customer ID `my_ID`:

```bash
curl -X DELETE -u "apikey:{apikey}" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/user_data?customer_id=my_ID&version=2018-03-19"
```
{: pre}

The `/v3/user_data` method deletes all data that is associated with the specified customer ID, regardless of the method by which the information was added. The method has no effect if no data is associated with the customer ID.

**Note**: Delete requests are processed in batches and might take up to 24 hours to complete.

### Support
{: #gdpr-visrec-support}

Please direct questions to your account representative, or reach out to support directly at [https://ibm.biz/ibmcloudsupport ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/ibmcloudsupport){: new_window}.
