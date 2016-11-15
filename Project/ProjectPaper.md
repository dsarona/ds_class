
## Improving Incident Identifcation and Resonse Time
There are limited security resources to monitor and respond to attacks on an increasing number of ephermal hosts and services. These hosts and services are cloud based using the [DevOps model](https://en.wikipedia.org/wiki/DevOps) for deployment and frequent change. All of which makes identifying the risk of these services more difficult before they are deployed and removes nearly all ability to manually identify issues in such an automated environment. 

So my theory is by reviewing hosts/services that are being targetted now we can be identify earlier on in the [cyber kill chain](https://en.wikipedia.org/wiki/Kill_chain) process those services or hosts to be compromised in the near future. Or put another way, being able to better identify those hosts and services most at risk as they are being automatically deployed. 

## Description of your data set and how it was obtained
* [Shodan](https://www.shodan.io/)
  * Public queries saved as CSV and downloaded
  * Data includes IP, domain and service details that are publicly searchable. Tool is commmonly used by attackers as part of the recon effort when considering a target
* [Public data on AS networks](https://en.wikipedia.org/wiki/Autonomous_system_(Internet))
 * Public data on which networks (ASN to IP address) are tied with any company or resource. Information is then fed into a tool like Shodan or uesd to execute new network scans
* Sanitized firewall data on network connections
  * Query by 'live' IP's collected in step one
  * Organized by GEO, Port dst, and frequency
  * Based on actual network/FW events showing traffic patterns

[Data repository on GitHub](https://github.com/dsarona/ds_class/tree/master/Project/data)

## Description of any pre-processing steps you took
* File Preparation
  * For Shodan data, execution of the right queries based on ASN followed by pulling down results in CSV. Because each ASN was its own report data combined into one CSV before import
* Data Review and Manipulation
  * Shodan Data
    * Slicing of banner field to create the Response column
    * Slicing of the host field to create the Domain column
    * Slicing of the banner field to create the webcode column
    * New columns based on 'webcode' and 'domain' - dummy values representing column entries
  * Firewall Data
    * By IP address all traffic for two 24 hour windows that matches the following:
        * Allow to DST IP at Adobe (based on live hosts from Shodan data)
        * Source from Russia or China GEO
        * Removal of outliers used for product activation
        * Anonymizing of all Russia/China traffic to 1 or 0 (1 = traffic present, 2 = nothing from that GEO)
* Data Import (grab from Shodan DF)
* Key fields to be used (y and x)
   * Targetted field for the Y, represents those IP's where FW traffic was allowed from China/Russian IP
   * X to be set with service type (production, dev or testing), service status (web response code), and which destination ports were used 

## What you learned from exploring the data, including visualizations
* There is a significant number of external hosts available that don't appear to provide a business purpose. At least not one tied to the web ports open - no website running or providing a valid response
* The amount of 'suspect' traffic from certain GEO's was much larger than expected. Would appear that recon activity is nearly non-stop in some cases

(visualizations still in progress)
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
Model Selected - http://scikit-learn.org/stable/modules/naive_bayes.html

Selection Process
* Review of data to be used - categorical and text predominately
* Data set size (relatively small)


## Your challenges and successes
Challenges
* Data manipulation was required to get the features need for the modeling, more of an expected challenge
* Unexpected volume of traffic by GEO, when initially conceived didn't believe there would be so much interesting traffic orginating from the China Russia GEO's

Successes
* Ability to collect and summarize data by ASN - including services that are live, service responses, possible issues or vulnerabilities
* Actual identification of security issues based on initial analysis (identified vulnerable system configs)

## Possible extensions or business applications of your project
* Ability to routinely collect and display data on all live IP's from the external perspective - just what is it we have publicly facing tat could be tagetted
* Improved understanding and baseline of recon activity on targets from specific GEO's
* Ability to apply the same logic using other GEO's and possibly actual incident results in the future

## Conclusions and key learnings
