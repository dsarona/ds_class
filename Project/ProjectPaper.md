
## Problem statement and hypothesis
Limited security resources to monitor and respond to attacks on a growing number of hosts and services
Virtual and Cloud solutions reducing deployment time and overhead - growth of the devops model (instant deployment)
No easy model for identifying at risk services once they are deployed - why are some hosts compromised and not others
Need to automate as much as possible - no time for manually reviewing data

Theory that with data review hosts/services that will be targeted can be identified early on in the cyber kill chain process allowing for more resources to be spent reviewing specific activity. Or put another way, being able to better identify those hosts and services most at risk.

## Description of your data set and how it was obtained
* Shodan
  * Public queries saved as CSV and downloaded
* Public data on AS networks
* Sanitized firewall data on network connections
  * Query by 'live' IP's collected in step one
  * Organized by GEO, Port dst, and frequency

## Description of any pre-processing steps you took
* Slicing of banner field to create the Response column
* Slicing of the host field to create the Domain column

* Key fields to be used (y and x)
* Identification of null fields
* Combining into one doc

To Do
1. Domain to values based on stage/prod/cloud
2. Web response values to 200 or other (1 or 2)
3. 

## What you learned from exploring the data, including visualizations
* Grouping by port - there are several common ports in this data (80, 443, 8080, 22) 
* Grouping by HTTP response
* Grouping by ASN
* Grouping by parent domain

## How you chose which features to use in your analysis
Looking for features that will help determine the following:
* Was the service or asset targeted based on service type
* Was the service or asset targeted based on web or service response
* Was the service or asset targeted based on domain details 

If any of these features indicate which hosts/services are to be targeted we can better define a review and mitigation strategy. 

## Details of your modeling process, including how you selected your models and validated them

## Your challenges and successes

## Possible extensions or business applications of your project

## Conclusions and key learnings
