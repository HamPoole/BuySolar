# Buy Solar

## Functional Description & Goals:

Buy Solar is an application to simplify the purchase of cheap renewable energy for companies & consumers.

An increase in renewable electricity, and growing energy efficiency, means negative energy prices during daylight
hours occur more often. When more renewable energy is supplied than people need, prices decrease dramatically.<sup>
1</sup> <sup>
2</sup>

![Graph of negative electricity events Australia](https://wattclarity.com.au/wp-content/uploads/2021/02/2021-02-17-NEMreview-NegativePrices-AllRegions-Trend.png)

Buy Solar has an aim to onboard energy intensive businesses & households in these moments>. The aim is to have them
consume electricity when the price is lowest.

Buy Solar's Objectives:

1. Onboard electricity consumers to receive timely data flows of real time (updated minute by minute/hourly) electricity prices.
2. Allow energy consumers to set price thresholds to start/stop energy intensive appliances based on the energy spot
   price.<sup>3</sup>
3. Increase consumer awareness of spot price electricity and its value.
4. Support solar energy by consuming excess solar power during periods of low prices.

## Current Context:

- The vast majority of consumers do not consume energy via real time prices. Instead, time of use
  power, with pre-priced daily intervals (morning, afternoon, evening etc), or a flat contracted rate, predominate.
- Furthermore, the technology and capability for real time power consumption has been available for decades.
  Many analog solutions exist, economists and retailers have explored spot time plans extensively.
- However, with the growth of solar energy, the benefit of "demand management" is increasing, and there are far greater
  opportunities with the oversupply of energy.

## System Overview: Provide a general description and functionality of the software system.

The software design is based on two primary components.

1. Standalone console application. Hostable server-side, and on Windows/MacOS personal computers.
2. A multiple operating system desktop application that extends the above, and allows use and configuration by
   non-technical users.

These components will allow consumers to access an API endpoint for their electricity prices, and enable/disable their
energy device automation solution.

## Design Considerations: Describe the issues that need to be addressed before creating a design solution:

### Assumptions and Dependencies: Describe any assumptions that may be wrong or any dependencies on other things.

1. "Actual customer price" APIs are available to use. This is not the case in many countries, and few providers provide
   real time energy to start with.
2. Software users can successfully automate their power consumption based on the thresholds this application provides.
    1. Automation of their solutions beyond triggering are out of scope. This could prove a considerable hurdle.
3. Customers willing to engage in demand management without an existing solution can be found. This is a real
   consideration, as the number of businesses/consumers that'll materially benefit from this, and do not have a
   commercial off the shelf option, may not be large.

### General Constraints: Describe any constraints that could have an impact on the design of the software.

- Distribution of finished software. If the software is made, how will people find out about it?
- Personal computer specific architectures. Is creating a desktop application feasible?
- Commercial, paid for alternatives are readily available.

## Architecture and Development.

#### Technology Choices

Rust console application to access public API endpoints easily and reliably. Simply achieved via the asynchronous
library [axum](https://github.com/tokio-rs/axum).

Rust [Tauri](https://tauri.app/) desktop applications for Windows and MacOS.  "It's Electron but good," framework for
desktop web applications. Flexible access to the Javascript ecosystem means it's a very good solution.

#### Solution choices.

Steps of the workflow

1. Access price API. Will require a window/equivalent for the user to type in their API details.
2. Poll the price API data on a user defined interval. Another window. Store the data in a .csv log for ease of loading
   into Microsoft Excel. Access 2-3 (?) most recent records for threshold setting.
    1. Indexed database for graphing a stretch goal, but likely to be of lower value than exposing the data via
       spreadsheet software.
    2. A pre-made spreadsheet is a low value, high usability solution.

3. Parsing the API response will be required. Both generic .JSON/XML/otherwise flattening, and direct data extraction.
   May unfortunately require a user facing feature, perhaps a "regex generation app" or similar to build API parsing
   rules.  (USA has a common standard for this).
4. Display the current/last x prices to the user. Have the user set the price threshold and configure other options.
5. Trigger the threshold. Will require another window for the user to configure "what" is being triggered. Filesystem
   executable or an HTTP Post for launching or controlling an application they will have to configure themselves.
    1. An option for taking a custom script for complex logic, price forecasting is extremely simple, makes sense as a
       stretch.

### Diagram:

![Diagram_image](https://imgur.com/1eEe4U2.jpg)

## State of market: Existing solutions and risks

Unfortunately, several applications exist that fill this niche.

- Schneider Electric. A very large conglomerate that includes a power control software business, has this feature tucked
  away in an obscure corner of their catalogue.
- EnergyOS, commercial software, provides off the shelf integration and features far in excess of this design.

EnergyOS has a superset of these features, and a low adoption rate. 8+ years old with very few customers/employees,
indicating a lack of interest.

Additionally, there's a widespread trend of power companies controlling access to real time power extremely closely. A
history of "bill shock" to utilities from trials of real time pricing <sup>3</sup> means utilities proactively avoid
easily accessible "price at your doorstep" APIs.

Boutique API interfaces allow electricity providers to heavily discourage common interfaces by retail consumers.

It's likely the overall trend is any commercial business that would significantly benefit from variable rate power, has
a software solution already integrated.

The software was also conceived with the idea that falling solar energy prices would create an increasingly urgent need
for adoption. However, many providers stand by ready and waiting in this area, currently serving commercial providers.

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

https://www.ea.govt.nz/consumers/my-electricity-bill/is-a-spot-price-contract-right-for-me/
https://www.ea.govt.nz/operations/wholesale/security-of-supply/spot-prices-and-the-wholesale-market-review/

https://www.cpuc.ca.gov/news-and-updates/all-news/cpuc-sets-stage-to-enable-widespread-demand-flexibility
Alipour, Manijeh, et al. "Hedging strategies for heat and electricity consumers in the presence of real-time demand
response programs." IEEE Transactions on Sustainable Energy 10.3 (2018): 1262-1270.

Alstone, Peter, et al. 2025 California Demand Response Potential Study-Charting California’s Demand Response Future.
Final Report on Phase 2 Results. Lawrence Berkeley National Lab.(LBNL), Berkeley, CA (United States), 2017.

Brown, Toby, et al. "International review of demand response mechanisms." Brattle Group Birm. (2015).-
Kathan, David, et al. "National action plan on demand response." The Federal Energy Regulatory Commission Staff,
Federal Energy Regulatory Commission, Washington, DC, Tech. Rep. AD09-10 (2010).

Nezamoddini, Nasim, and Yong Wang. "Real-time electricity pricing for industrial customers: Survey and case studies in
the United States." Applied energy 195 (2017): 1023-1037.

SAN FRANCISCO, C. A. "ORDER INSTITUTING RULEMAKING." (2014).

Samad, Tariq, and Sila Kiliccote. "Smart grid technologies and applications for the industrial sector." Computers &
Chemical Engineering 47 (2012): 76-84.

Shafie-khah, Miadreza, et al. "Comprehensive review of the recent advances in industrial and commercial DR." IEEE
Transactions on Industrial Informatics 15.7 (2019): 3757-3771.

Siddiquee SMS, Howard B, Bruton K, Brem A and O’Sullivan DTJ (2021) Progress in Demand Response and It’s Industrial
Applications. Front. Energy Res. 9:673176. doi: 10.3389/fenrg.2021.673176

Snow, Stephen, et al. "Do solar households want demand response and shared electricity data? Exploring motivation,
ability and opportunity in Australia." Energy Research & Social Science 87 (2022): 102480.

Wang, Ge, et al. "The impact of social network on the adoption of real-time electricity pricing mechanism." Energy
Procedia 142 (2017): 3154-3159.

Wilkenfeld, G. "Mandating demand response interfaces for selected appliances: Consultation regulation impact
statement." E3 Committee, Canberra (2013).

https://utilityapi.com/docs
https://www.greenbuttonalliance.org/about
https://en.wikipedia.org/wiki/Open_Automated_Demand_Response
https://www.energyos.com.au/
