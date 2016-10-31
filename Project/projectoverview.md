# Prediciting Targetted Attacks - Moving Down the CyberKill Chain

## Problem Statement
* Limited security resources to monitor and respond to attacks on a growing number of hosts and services
  * Virtual and Cloud solutions reducing deployment time and overhead - growth of the devops model (instant deployment)
  * No easy model for identifying at risk services once they are deployed - why are some hosts compromised and not others
  * Need to automate as much as possible - no time for manually reviewing data 
 


## Proposed Measurements
Determine if publicly available traits for a host or service can be correlated with a propensity for attack and targetting. In this case do the publicly available traits for a service correlate with netflow to/from IP's in specific GEO's. If successful can be used to quickly identify hosts or traffic for further review and which hardening efforts for a service might pay off immediately. 

* Examples:
 * Does it matter if a host or service doesn't return a valid response? 
 * Does it appear if Apache, IIS or some other platform are used? 
 * Are there some hosts or services that seem to be targetted less than others? 
 
In this case targetted is defined as logged traffic orginating from remote GEO (Russia/China) in scope hitting a host with a live IP more than once. 


## Data in Scope
* Public data on service and hosts 
 * [Shodan](https://www.shodan.io/search?query=ASN%3AAS7233)
 * [Info for an ASN](https://mxtoolbox.com/SuperTool.aspx?action=asn%3ayahoo&run=toolpage)
 
* Firewall data on network connections
 * Query by 'live' IP's collected in step one
 * Organized by GEO, Port dst, and frequency
   
## Considerations and Assumptions
Considerations
* By using all of the live IP's for an ASN removes possibly network bias - so not just part of a network or service targetted
* Focusing on publicly available data means it is widely scanned and attacked
* Possibly find actual compromise during exercise

Assumptions
* There are some discernable differences, not everything is targetted at the same or similar levels
* There is limited legitimate traffic from specific GEO's in scope

Long term this information could possibly be improved by also flagging those hosts/services that have been known to be compromised. 

## Next Steps
* Data collection and manipulation
 * Removing possible null values
 * Seperating out all key host/service attributes
 * Based on live IP's collecting FW/Network actiity for the same period of time (after anonymoyzing)
* Refining collection window 
 * 30 days looks like a good fit
 * Determining if any hosts have actually been compromised
* Model selection and testing
