---
title: Common errors
pcx_content_type: reference
type: overview
weight: 2
---

# Common errors

Refer to the information below for more details on common notification errors and how to troubleshoot them.

## Webhook test failed with status code 400 400 Bad Request

This error can occur when you try to configure a webhook that is not currently supported, such as setting up a PagerDuty webhook.

PagerDuty needs to be configured under [connected notification services](/notifications/get-started/configure-pagerduty/).

## Deleted users are still receiving notifications

When you remove a user from your account via **Manage Account** > **Members** in the Cloudflare dashboard, their email address is not removed from existing notifications.

You need to remove the email address from the configuration of the notifications by [editing the notification recepient](/notifications/get-started/#edit-a-notification).