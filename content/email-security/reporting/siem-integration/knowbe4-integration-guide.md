---
title: KnowBe4
pcx_content_type: integration-guide
meta:
    description: KnowBe4 integration guide
updated: 2023-08-04
---
# KnowBe4

When Area 1 detects a {{<glossary-tooltip term_id="phishing">}}phishing{{</glossary-tooltip>}} email, the metadata of the detection can be sent directly to KnowBe4. For this tutorial, you will need a working KnowBe4 account with the SecurityCoach add-on. You will also need to create an organization key to use in Area 1. This organization key will let you integrate KnowBe4 with Area 1. Refer to [KnowBe4 documentation](https://support.knowbe4.com/hc/articles/13129840202643) for more information on this subject.

After creating your organization key and authorizing Area 1:

1. Log in to the [Area 1 dashboard](https://horizon.area1security.com/).
2. Go to **Settings** (the gear icon).
3. Go to **Email Configuration** > **Domains & Routing** > **Alert Webhooks**.
4. Select **New Webhook**.
5. In **App Type**, select **SIEM**.
6. Choose _KnowBe4_ from the dropdown, and paste your organization key into the **Auth Code** section.
7. In **Target**, paste the URL that suits your organization. KnowBe4 has different URLs for different regions:
    KnowBe4 instance | URL
    ---              | ---
    United States    | `https://area1.vendor.training.knowbe4.com/v1`
    European Union   | `https://area1.vendor.eu.knowbe4.com/v1`
    Canada           | `https://area1.vendor.ca.knowbe4.com/v1`
    United Kingdom   | `https://area1.vendor.uk.knowbe4.com/v1`
    Germany          | `https://area1.vendor.da.knowbe4.com/v1`
8. Select _Expanded_ from the drop-down menu for **Malicious Style**, **Suspicious Style**, and **Spoof Style**.
9. Select **Publish Webhook**.