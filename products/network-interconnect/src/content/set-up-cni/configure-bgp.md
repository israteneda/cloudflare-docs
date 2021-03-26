---
title: Configure BGP
order: 5
---

# Configure the Border Gateway Protocol (BGP) and Generic Route Encapsulation (GRE)

After establishing your connection, the next steps include provisioning the GRE IPs and configuring the BGP peering information. This process takes approximately one week.

## Provision the IP

Cloudflare sends a set of IPs that you assign to your connection before Cloudflare establishes the BGP connection. The set of IPs will look similar to the example below.

```
Cloudflare v4: 108.162.247.10/31
iManage v4: 108.162.247.11/31
Cloudflare v6: 2400:cb00:26:3::6ca2:f70a/127
iManage v6: 2400:cb00:26:3::6ca2:f70b/127
```

Assign the set of IPs to your connection. Next, perform a series of ping tests to ensure the connection is established. Although you may see the green connection from [configuring the cross-connect](/set-up-cni/configure-x-connect.md), the ping tests confirm packets are flowing over the link.

If you have a virtual link via Megaport, the IP provisioning may fail if you have not configured the VLAN with the VLAN provided by your Customer Success Manager.

## Configure the BGP

After you provision the IPs and the ping tests confirm the connection, accept the routes from the BGP session Cloudflare configured. Configuring the BGP session on both the Cloudflare and user sides requires a BGP call and a ~two hour maintenance window that you provide to Cloudflare. 

Cloudflare advertises all of its prefixes over the CNI, but the process occurs over a private link from Cloudflare to the customer data center.

<Aside type="note">

Why does my CNI need to accept all of Cloudflare's prefixes? Accepting all of Cloudflare's prefixes ensures your CNI is fully utilized, and traffic routed from PoPs back to the CNI is secure, fast, and realiable.

</Aside>

After you accept the BGP session, traffic begins flowing over the CNI. To confirm traffic is flowing correctly, you can contact your solutions engineer who can see whether or not traffic is flowing.

## Go live

When traffic begins flowing over the connection, you are fully set up with CNI!