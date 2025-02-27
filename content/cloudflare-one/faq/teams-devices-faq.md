---
pcx_content_type: faq
title: Devices
weight: 6
meta:
    description: Review frequently asked questions about devices in Cloudflare Zero Trust.
---

[❮ Back to FAQ](/cloudflare-one/faq/)

# Devices

## Why does my Windows device appear to switch from Wi-Fi to Ethernet when I enable WARP?

As the WARP client has replaced WinDivert with WinTun architecture, all Windows machines using WinTun will show as being connected using a virtual adapter. Windows, by default, shows virtual adapter connections with a wired Ethernet connection icon, even if the device is connected over wireless. This is by design and should have no impact on connectivity.

## Why is my device not connecting to a closer Cloudflare data center?

As our [Network Map](https://www.cloudflare.com/en-gb/network/) shows, we have locations all over the globe. However, in the Advanced Connection stats of our application, you may notice that the data center (colo) you are connecting to isn't necessarily the one physically closest to your location. This can be due to a number of reasons:

- Sometimes your nearest colo may be undergoing maintenance or having problems. Check [here](https://www.cloudflarestatus.com/?_ga=2.155811579.1117044671.1600983837-1079355427.1599074097) for system status.
- Your Internet provider may choose to route traffic along an alternate path for reasons such as cost savings, reliability, or other infrastructure concerns.

## Why is my public IP address sometimes visible?

Cloudflare WARP Client in WARP mode was meant to ensure all your traffic is kept private between you and the origin (the site you are connecting to), but not from the origin itself. In a number of cases, if the origin site you are communicating with can't determine who you are and where you're from, they can't serve locale relevant content to you.
Sites inside Cloudflare network are able to see this information. If a site is showing you your IP address, chances are they are in our network. Most sites outside our network (orange clouded sites) however are unable to see this information and instead see the nearest egress colo to their server. We are working to see if in the future we can't find a way to more easily share this information with a limited number of gray clouded sites where it is relevant to both parties.

## Why has my throughput dropped while using WARP?

Cloudflare WARP is in part powered by 1.1.1.1. When visiting sites or going to a new location on the Internet, you should see blazing fast DNS lookups. However, WARP is built to trade some throughput for enhanced privacy, because it encrypts all traffic both to and from your device. While this isn't noticeable at most mobile speeds, on desktop systems in countries where high speed broadband is available, you may notice a drop. We think the tradeoff is worth it though and continue to work on improving performance all over the system.

## Why is my device not connecting to a public Wi-Fi?

The Wi-Fi network may have a captive portal that is blocking WARP from establishing a secure connection. In order to access the portal, and therefore the Internet, you will need to temporarily turn off WARP. After you login to the captive portal through your browser, you can turn WARP back on to access corporate resources.

For more information, refer to [Captive portal detection](/cloudflare-one/connections/connect-devices/warp/configure-warp/warp-settings/captive-portals/).

## Why is my device not connecting to the Internet?

A third-party service or ISP may be blocking WARP, or Zero Trust settings may be misconfigured. For a list of common issues and steps to resolve, refer to our [troubleshooting guide](/cloudflare-one/connections/connect-devices/warp/troubleshooting/common-issues/).

## Why is my device not connecting to the corporate Wi-Fi?

An [OS firewall rule](/cloudflare-one/connections/connect-devices/warp/configure-warp/route-traffic/warp-architecture/#system-firewall) on the device may be blocking the EAP/Radius server that allows users to join the Wi-Fi network. If your corporate Wi-Fi uses a Radius server for network authentication, add the Radius server to your [Split Tunnel](/cloudflare-one/connections/connect-devices/warp/configure-warp/route-traffic/split-tunnels/) Exclude list.

## Why is my device not connecting to my private network?

If your private network is [exposed via Cloudflare Tunnel](/cloudflare-one/connections/connect-networks/private-net/cloudflared/):

- Verify that the WARP client is [properly configured](/cloudflare-one/connections/connect-networks/private-net/cloudflared/#device-configuration) on the device.
- Verify that the user is allowed through by your Access and Gateway policies.
- Verify that the [local LAN settings](/cloudflare-one/connections/connect-networks/private-net/cloudflared/#router-configuration) for the device do not overlap with the CIDR range of your private network.

When contacting Cloudflare support, ensure that you include [WARP debug logs](/cloudflare-one/connections/connect-devices/warp/troubleshooting/warp-logs/) for your device. These logs will help Cloudflare support understand the overall architecture of your machine and networks.
