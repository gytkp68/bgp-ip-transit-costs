# BGP IP Transit: What It Costs, Do You Need Your Own ASN, and When a BGP-Capable VPS Is the Better Buy

A UK provider's public price list puts BGP IP transit at £75/month for 100 Mbps, £130/month for 1 Gbps and £800/month for 10 Gbps, with cross-connects billed on top. Almost nobody else in this market publishes numbers at all, which is why "how much does IP transit cost" usually gets answered with a quote form.

Most people who search for this term don't end up buying transit. They run a game server, a small SaaS edge or a China-facing service, they want a real BGP session rather than a consumer uplink, and they discover that a carrier contract starts at four figures a month with a twelve-month commit and a cross-connect they have to order from the data centre themselves. That group needs a host that will hand off a BGP session and let them announce their own prefix.

Below: what a transit contract actually includes, how to tell whether you need one, what the published price ladder says about per-Mbps economics, and where SixtyNet's BGP-capable Los Angeles plan fits for readers who want the session without the contract.

> **Quick pick.** SixtyNet's Los Angeles China Unicom-Premium VPS is the one plan in its catalogue built for BGP: free BGP session setup, an AS9929 China Unicom path, 100 Mbps base with 3× burst on 95th-percentile billing, $2,500/year against a $3,000 list price. It is a hosted BGP endpoint, not a multi-upstream transit contract, and the product page describes BGP technical support as limited.
> 👉 See SixtyNet's BGP-capable plan and current pricing

## What SixtyNet actually sells, and which plan is for BGP

SixtyNet is a hosting provider with its own small network (AS60699, six announced prefixes through two upstreams in third-party routing data). Its published catalogue is VPS and residential-IP hosting. There is no committed-bandwidth transit product with a full-table BGP feed and a defined SLA on its pricing pages, so if you need two upstreams, a 10G port and a contract, you are shopping elsewhere. What it does sell is a way to get a BGP-speaking box in Los Angeles with a China-optimised path, priced annually.

Every plan currently shown on the VPS hosting page is in the table below. Prices are USD as displayed; the annual figure is what the page charges, and the monthly equivalents for the residential line come from its own cart page.

| Plan | vCPU / RAM / NVMe | Network & transfer | Price (USD) | Billing | Order |
| --- | --- | --- | --- | --- | --- |
| **Los Angeles China Unicom-Premium** | not published; 100 Mbps base, 3× burst | AS9929 China Unicom premium, free BGP session setup, limited BGP support | **$2,500** (list $3,000, −17%) | Annual | [Order](https://sixtynet.net/aff.php?aff=39) |
| Residential-STARTER | 2 core / 2 GB / 40 GB | 2 Gbps, 5 TB, residential IP | $260 (list $300; $25/mo) | Annual | [Order](https://sixtynet.net/aff.php?aff=39) |
| Residential-MICRO | 4 core / 4 GB / 80 GB | 4 Gbps, 10 TB, residential IP | $460 (list $540; $45/mo) | Annual | [Order](https://sixtynet.net/aff.php?aff=39) |
| Residential-MEDIUM | 8 core / 8 GB / 160 GB | 10 Gbps, 20 TB, residential IP | $860 (list $1,020; $85/mo) | Annual | [Order](https://sixtynet.net/aff.php?aff=39) |
| Residential-LARGE | 16 core / 16 GB / 320 GB | 10 Gbps, 40 TB, residential IP | $1,660 (list $1,980; $165/mo) | Annual | [Order](https://sixtynet.net/aff.php?aff=39) |
| IRVINE-PRO-STARTER | 2 core / 2 GB / 40 GB | 2 Gbps, 5 TB, AS9929 China-optimised, residential IP | $350 (list $420) | Annual | [Order](https://sixtynet.net/aff.php?aff=39) |
| IRVINE-PRO-MICRO | 4 core / 4 GB / 80 GB | 4 Gbps, 10 TB, AS9929 China-optimised, residential IP | $550 (list $660) | Annual | [Order](https://sixtynet.net/aff.php?aff=39) |
| LAX-STARTER | 2 core / 2 GB / 40 GB | 2 Gbps, 5 TB, DDoS protection | $200 (list $240) | Annual | [Order](https://sixtynet.net/aff.php?aff=39) |
| LAX-MICRO | 4 core / 4 GB / 80 GB | 4 Gbps, 10 TB, DDoS protection | $400 (list $480) | Annual | [Order](https://sixtynet.net/aff.php?aff=39) |
| LAX-MEDIUM | 8 core / 8 GB / 160 GB | 10 Gbps, 20 TB, DDoS protection | $800 (list $960) | Annual | [Order](https://sixtynet.net/aff.php?aff=39) |
| LAX-LARGE | 8 core / 16 GB / 320 GB | 10 Gbps, 40 TB, DDoS protection | $1,600 (list $1,920) | Annual | [Order](https://sixtynet.net/aff.php?aff=39) |
| LAX-Storage-500G | 4 core / 4 GB / 300 GB + 200 GB RAID 10 | 10 Gbps, 10 TB, DDoS protection | $400 (list $480) | Annual | [Order](https://sixtynet.net/aff.php?aff=39) |
| LAX-Storage-1TB | 8 core / 8 GB / 700 GB + 300 GB RAID 10 | 10 Gbps, 15 TB, DDoS protection | $700 (list $840) | Annual | [Order](https://sixtynet.net/aff.php?aff=39) |

Three limitations belong next to those numbers. The residential-IP plans **do not open ports 80 and 443** because of IP risk controls, so they cannot serve ordinary public web traffic. The IRVINE-PRO line refunds to account balance only, not to your card. And the $2,500 on the BGP-capable plan is an annual figure; at roughly $208/month equivalent you are paying for the AS9929 path and the China latency profile, not for bandwidth volume.

> 👉 Check what's currently in the SixtyNet catalogue before comparing it against a transit quote

## Do you need IP transit at all?

The dividing line between IP transit and dedicated internet access is control over public routing, not bandwidth. A company that needs Microsoft 365, SaaS, VPN and cloud access to work reliably has no reason to run BGP on the public internet; DIA covers it, usually without an ASN. A company that announces its own prefixes, compares routes from several upstreams and applies BGP communities to steer inbound traffic needs transit, because that is the product that gives it a routing policy.

Providers often split the offering four ways, which is a useful checklist when you read a quote:

- **Full transit** — complete BGP table, full routing control, the classic product.
- **Partial transit** — direct routes to the provider's own peering only, used as a supplement to an existing transit service rather than a replacement.
- **Out-of-band** — a small 10 Mbps port with a /30 for reaching remote routers when the main circuit is down.
- **DIA** — internet access with a /30, no ASN required.

Size doesn't settle it. A large enterprise can have no business reason to manage internet routes, while a two-person game studio whose revenue depends on latency to specific networks has a strong case for its own ASN, portable address space and two upstreams. The test is whether you have a reason to exercise control, and whether you can staff the work: route policy, prefix validation, upstream monitoring, and understanding why a prefix disappeared at 3am.

## Full table, partial routes, or a default route

Taking a full BGP table is not mandatory, and for many buyers it's waste. A single-homed customer storing more than a million IPv4 routes gains almost nothing, because it has one path out. A multihomed network wants the full table precisely so it can choose between paths learned from different providers.

Smaller options exist and are cheaper to run: a default route only, or a partial feed of the provider's directly connected routes. Ask which one you're being quoted. A "full BGP table" line on a proposal for a single-uplink office is a sign nobody read your requirements.

## Your ASN and your /24 decide whether you can ever switch providers

If your public addresses are assigned by the transit provider, changing providers means renumbering everything behind them. If you hold a portable prefix and advertise it through two providers, you can withdraw it from one and keep the same addresses in service. For anything with paying users, DNS TTLs, allowlists or customer firewall rules, that portability is worth more than a few pounds per Mbps.

This is also where quotes get slippery. One UK provider's site states in its ordering steps that it supplies "a /24 or larger IPv4 block + full IPv6", then states in its own FAQ that you need your own ASN and at least a /24 prefix. Both sentences are on the same page. Whichever applies to your order, get it in writing before you sign: who owns the addresses, who can take them away, and what happens to them if you leave.

A BGP-capable VPS sidesteps part of this. You're renting a session, not an address block, and the provider's ASN does the announcing unless you have your own. It also means you are single-homed by definition and inherit whatever path that host has.

## What BGP IP transit costs per Mbps, and what the quote leaves out

The one public price list I could verify (VeloxServ, AS3170, on-net UK locations, free setup, cross-connects excluded) is a clean illustration of how transit is priced. The per-Mbps figures below are my arithmetic on their published monthly rates, not figures the provider states:

| Committed rate | Port | Monthly | £ per Mbps |
| --- | --- | --- | --- |
| 100 Mbps | 1 × 1 Gbps | £75 | £0.75 |
| 500 Mbps | 1 × 1 Gbps | £100 | £0.20 |
| 1 Gbps | 1 × 10 Gbps | £130 | £0.13 |
| 2 Gbps | 1 × 10 Gbps | £220 | £0.11 |
| 5 Gbps | 1 × 10 Gbps | £450 | £0.09 |
| 10 Gbps | 2 × 10 Gbps | £800 | £0.08 |
| Custom | 2 × 100 Gbps | quote | — |

The 100 Mbps tier costs about nine times more per Mbps than the 10 Gbps tier. That is the whole argument against signing a big port "in case traffic grows": you pay the small-port premium only while you are small, and upgrading later is a port reconfiguration, not a new contract negotiation.

What the monthly rate excludes matters as much as the rate. Cross-connects are billed separately and are not included in that table. Add the data centre cross-connect, the router or the optics, DDoS mitigation if it isn't bundled, and the commit term. A headline $/Mbps comparison that ignores those lines can invert the ranking of two quotes.

## Commit plus burst, or 95th percentile

Two billing models dominate. Flat rate is a fixed monthly figure for a fixed rate. Commit-plus-burst lets you commit to a level and pay an agreed rate for traffic above it. 95th-percentile billing discards the top 5% of samples and bills the rest, which rewards short spikes and punishes sustained growth.

The choice matters most for spiky traffic. A service with a 30-minute peak every evening fits 95th percentile well. A service that grows steadily will cross its committed rate and stay there, at which point the burst rate becomes the bill, and re-committing is the cheaper move. SixtyNet's BGP-capable Los Angeles plan uses 95th-percentile billing with a 3× burst allowance on a 100 Mbps base, which is workable for bursty regional traffic and tight for sustained volume.

## How to vet a provider in a market of self-reported numbers

Nearly every number on a transit provider's homepage is self-reported and defined differently by each company. One provider advertises 10,000+ direct peers and 100+ internet exchanges alongside 350 Gbps of daily traffic; another quotes 50+ points of presence and "thousands" of networks with no public pricing at all. Neither set is comparable to the other, and neither tells you which route your traffic to a specific access network will take.

Two checks are worth more than any of those figures.

**Physical diversity.** Two providers can hand you identical 100G ports in the same building and still share conduit, a meet-me room or an upstream. Ask for the physical path: customer router, optic, cross-connect, meet-me room, carrier edge, provider backbone. If both circuits traverse the same duct, you have one circuit and two invoices.

**Route-level evidence.** Ask each provider for looking-glass output or a traceroute to your ten most important destination networks, and compare. Internet routing is frequently asymmetric, and reachability runs both ways: you need routes to the internet, and the internet needs routes back to your prefix. Those paths are not guaranteed to match.

Tier labels are not a quality rating. A Tier 1 network may have superb global coverage and still hand your traffic to a regional operator with better local fibre and deeper local peering. Judge on measured latency to your actual users, not on a tier number that providers apply to themselves inconsistently.

## FAQ

**Do I need my own ASN for BGP IP transit?**
For a multi-upstream transit contract, generally yes, and you also need a portable prefix you can advertise. For a hosted BGP session on a VPS, often no, because the provider announces from its own ASN. Confirm which side owns the ASN and the addresses before ordering, since published pages contradict each other on this.

**Can peering replace transit?**
No. Peering exchanges traffic with the networks you have a relationship with; transit reaches everything else. Settlement-free peering isn't free either, since routers, ports, transport, colocation and cross-connects all cost money. Most networks run both.

**Is 100 Mbps enough to start?**
For a BGP session, a game server cluster, or a small SaaS edge, yes. It is also the most expensive tier per Mbps, so treat it as a starting point with a defined upgrade path rather than a destination.

**How fast is provisioning?**
A UK provider advertising on-net data centre ports quotes "a few business days" for most on-net locations. Cross-connects and off-net transport extend that. Hosted VPS delivery is a different process entirely and doesn't depend on a carrier lead time.

**Why does the same provider give different answers about IP addresses?**
Because product pages, ordering flows and FAQs are often written by different teams at different times. The contract, not the web page, decides.

## Which option fits your situation

- **One office, one app, no public prefixes** → DIA. You get reliability without the operational weight of public routing, and BGP remains optional.
- **Public services, one upstream, no plans to switch** → full or partial transit with provider-assigned addresses is fine, and cheaper to start.
- **Public services you may need to move between providers** → your own ASN plus a portable /24, announced to at least two upstreams with genuinely separate physical paths.
- **A BGP session or a China-optimised path without a carrier contract** → a hosted BGP-capable VPS is the lower-commitment route, accepting that you're single-homed and that support for routing questions may be limited.

Two things to confirm in writing before you pay anyone: who owns the IP addresses and what happens to them if you leave, and whether the second "redundant" upstream really takes a different physical path. Both are cheap to ask about now and expensive to discover later.

👉 Compare SixtyNet's BGP-capable Los Angeles plan against your current quote
