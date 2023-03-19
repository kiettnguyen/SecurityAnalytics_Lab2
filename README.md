# SecurityAnalytics_Lab2
You are a threat intel analyst / security engineer / data scientist / threat hunter (how many more titles can we add?) at a company that captures PCAPs and Zeek (formerly Bro logs) from their endpoints.

## Part 1: SIEM

In the first part of this lab, you are tasked by your manager with setting up a SIEM (security information and event management) and loading a PCAP from a recent incident. You will need to write a brief report in a digestible format for your manager / CISO about the recent incident that was flagged by the endpoint's AV (antivirus).

### 1. Setup/Access
Make a free trial Splunk account and install Splunk Enterprise from [here](https://www.splunk.com/en_us/download/splunk-enterprise.html)
Follow the installation instructions for your OS
Run Splunk
Navigate to "Find More Apps" in the top left corner
Search for "pcap" and install the "PCAP Analyzer for Splunk" app

### 2. SIEM Assignment
We have provided the PCAP that the endpoint captured when the incident occurred in NYU classes.
Follow the installation instructions above.
Write a technical analysis to share with your CISO outlining the attacker's tactics.
Explain exactly what happened but do this in high-level detail in a digestible report because you are talking to a CISO. Provide evidence of all your claims!
Hint: Make statements like: the infection started at X date time because of XYZ connection. The packets before this seem normal because of ABC.

## Part 2: Data Processing (Spark)

In the second part, your manager has explained that the CISO wants you to investigate the threat that targeted your company. To do this, you need to take advantage of the Zeek logs and big data processing tools like Spark to actively hunt for more indicators about the threat and tell a more thorough story about potential bad actors.

### Setup

Locate the **spark_demo.ipynb** file for an introduction and instructions.

### Load data

[Zeek](https://zeek.org/) (formerly Bro) is a powerful network analysis tool. In this scenario, your network admin had
Zeek setup capturing logs. So you also have access to Zeek logs which are fairly easy to
convert to CSV. The logs can be found in this lab's section in NYU classes. Use the following
tool to convert the Zeek (bro) logs to CSV: https://github.com/geekscrapy/bro2csv . Now you will
be able to load the CSVs using Spark.
Note: There are 5 Zeek logs (conn, dhcp, dns, files, http) in total. Convert all of these to CSV
and use them all in your threat hunting.

### Spark Assignment

OSINTs (Open-Source Intelligence) such as:
* VirusTotal
* Shodan
* Greynoise

These services all have APIs that we can use for scripting in Python with pyspark. Spark installation instructions can be found here (or `brew install spark` on a mac). You can create a free account for the APIs. We suggest starting with VirusTotal. With VirusTotal, you will need to use caching to avoid hitting the daily rate limit.

Turn in:
* A jupyter notebook where you have identified additional IOCS from the zeek logs using pyspark scripting and the above APIs.
* You need to get IOCs from every row where it is possible. This is why you should use caching (mentioned above). Show examples of caching in your notebook.
* The notebook should have some cells where you output counts and statistics around these OSINT discovered IOCs 

In a separate document from the notebook, write a brief report using these OSINT IOCs.
Hypothesize what the threat is. Back up your claims with evidence.

Hint: Use spark to output some analyses about trends in the IOC related info you collect from the OSINT tools. Any majority IOCs you see based on the network information may give you clues as to what malware types could have been captured by these logs.
