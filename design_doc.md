# Buy Solar

## Functional Description & Goals:

Buy Solar's an application to demonstrate & simplify the purchase of cheap renewable energy for businesses & consumers
as the price fluctuates daily.

Growing renewable energy supplies, and increasing consumer efficiency, means negative energy price events, where more
renewable energy is supplied than needed, are increasingly common.<sup>1</sup> <sup>2</sup>

![Graph of negative electricity events Australia](https://live-production.wcms.abc-cdn.net.au/bb66f38c5bf6228c5df54a69af8c0c63?src)

Buy Solar's goal is to onboard energy intensive businesses & households to consume electricity when the price is right.
Its goals are:

1. Onboard electricity consumers to have timely data flows of real time electricity prices.
2. Allow energy consumers to set price thresholds to start and stop energy intensive appliances based on the energy spot
   price.<sup>3</sup>
3. Drive growth with businesses and consumers who have not previously participated in consuming electricity based on the
   spot price.

## Current Context:

- Vast majority of consumers do not consume energy via Real Time Prices marked to the daily supply. Instead, Time Of Use
  power, with pre-priced daily intervals, or a flat contracted rate, predominate.
- Furthermore, the technology and capability for real time power consumption has been available and studied for decades.
  Many analog solutions exist, economists and retailers have explored real time plans for decades.
- However, with the growth of solar energy, the benefit for "demand management," increasing and decreasing workloads
  depending on supply, will increase heavily due to the variable oversupply of energy.

## System Overview: Provide a general description and functionality of the software system.

The software design is based on two primary components.

1. Standalone console application. Hostable server-side and on Windows/MacOS personal computers.
2. A multi-operating sytstem desktop application that extends the above, and allows use and configuration by
   non-technical users.

These components will allows consumers to access an API endpoint for their electricity prices, and enable/disable their energy device automation solution.

## Design Considerations: Describe the issues that need to be addressed before creating a design solution:

### Assumptions and Dependencies: Describe any assumptions that may be wrong or any dependencies on other things.

1. "Actual customer price" APIs are available to use. This is not the case in Australia, and is the case in New Zealand
   with only one provider.
2. Software users can successfully automate their power consumption based on the thresholds this application provides.
   Automation of their solutions beyond triggering is out of scope.
3. Customers willing to engage in demand management without an existing solution can be found. This is a real
   consideration, as the number of businesses/consumers that'll materially benefit from this, and do not have a
   commercial off the shelf option, may not be large."

### General Constraints: Describe any constraints that could have an impact on the design of the software.

- Distribution of finished software. If the software is made, how will people find out about it?
- Personal computer specific architectures. Is creating a desktop application feasible?
- Commercial, paid for alternatives are readily available.


## Architecture and Development.

Rust console application to access public API endpoints easily and reliably. Simply achieved via the asynchronous
library [axum](https://github.com/tokio-rs/axum).

Rust [Tauri](https://tauri.app/) desktop applications for Windows and MacOS.

Parsing the API response will be required.  Requires a regex generation app or similar to build API parsing rules.

Requires a way to trigger home power applications.  May need to trigger a filesystem file or HTTP POST

### Diagrams of GUI:

![Diagram_image](https://imgur.com/HSz9kKh.jpg)

## State of market: Existing solutions and risks

Demand side management, demand response

https://github.com/topics/energy-management?o=desc&s=stars

http://wattdepot.org/

https://github.com/bemoss/BEMOSS3.5

https://github.com/emoncms/emoncms

Home energy management system.

Paid Companies

https://www.ohmconnect.com/

https://www.enode.io/blog/demand-response-software

Glossary: An ordered list of defined terms and concepts used throughout the document.

#### References

[1] https://aemo.com.au/newsroom/news-updates/negative-electricity-demand-in-south-australia
[2] https://www.energycouncil.com.au/analysis/increases-in-negative-prices-is-it-a-positive/
[3] Barbose, Galen, Charles Goldman, and Bernie Neenan. A survey of utility experience with real time pricing. No.
LBNL-54238. Lawrence Berkeley National Lab.(LBNL), Berkeley, CA (United States), 2004.

A Real-Time Consumer Control Scheme for Space Conditioning Usage
under Spot Electricity Pricing

#### Resources/Bibliography

https://www.ea.govt.nz/consumers/my-electricity-bill/is-a-spot-price-contract-right-for-me/
https://www.ea.govt.nz/operations/wholesale/security-of-supply/spot-prices-and-the-wholesale-market-review/

https://www.cpuc.ca.gov/news-and-updates/all-news/cpuc-sets-stage-to-enable-widespread-demand-flexibility

Siddiquee SMS, Howard B, Bruton K, Brem A and O’Sullivan DTJ (2021) Progress in Demand Response and It’s Industrial
Applications. Front. Energy Res. 9:673176. doi: 10.3389/fenrg.2021.673176

https://utilityapi.com/docs
https://www.greenbuttonalliance.org/about
https://en.wikipedia.org/wiki/Open_Automated_Demand_Response

https://www.energyos.com.au/
Real-time electricity pricing for industrial customers: Survey and case
studies in the United States