
### Buy Solar

#### Functional Description & Goals:

Buy Solar is an application to demonstrate & simplify the purchase of renewable spot price energy for consumers and businesses.  Negative energy pricing events are a feature of modern energy markets, as variable renewable energy sources produce
demand when available.<sup>1</sup> <sup>2</sup> 

Buy Solar's goal is allowing energy intensive businesses & households to consume electricity when the price
is below their set threshold

#### System Overview: Provide a general description and functionality of the software system.

The software is based on two primary components.  

1. Standalone console applicationm hostable both run server-side and on Windows/MacOS personal desktops.  
2. Desktop application that extends the above, and allows demonstration and configuration by non-technical users. 

#### Design Considerations: Describe the issues that need to be addressed before creating a design solution:

    Assumptions and Dependencies: Describe any assumptions that may be wrong or any dependencies on other things.
    Spot power price is available
    General Constraints: Describe any constraints that could have an impact on the design of the software.
    Users shut down their desktops at the end of the day.  
    Applications may be started then the software goes offline.

    Goals and Guidelines: Describe any goals and guidelines for the design of the software.
    Goal is to demonstrate to nontechnical users that this works with working software.
    Must be usable by nontechnical users.  "Tech native" users are already catered to.

    Must work on Windows and MacOS, whilst being hostable on Unix servers.

    Development Methods: Describe the software design method that will be used.

    Rust console application to access public API endpoints easily and reliably.  

    Rust Egui desktop applications for Windows and MacOS.

A software design document Architectural Strategies: Describe the strategies that will be used that will affect the system.

Application is independent of the graphical interface.

System Architecture: This section should provide a high-level overview of how the functionality and responsibilities of the system were partitioned and then assigned to subsystems or components.

Policies and Tactics: Describe any design policies and/or tactics that do not have sweeping architectural implications (meaning they would not significantly affect the overall organization of the system and its high-level structures).

Detailed System Design: Most components described in the system architecture section will require a more detailed discussion. Other lower-level components and subcomponents may need to be described as well.

Glossary: An ordered list of defined terms and concepts used throughout the document.

#### References
[1] https://aemo.com.au/newsroom/news-updates/negative-electricity-demand-in-south-australia 
[2] https://www.energycouncil.com.au/analysis/increases-in-negative-prices-is-it-a-positive/