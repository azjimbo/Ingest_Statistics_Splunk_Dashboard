Finding missing data (or other ingest anomolies) based on Z Score*.

There are two versions of this dashboard.   The first uses a scheduled search that populates a summary index. The scheduled search that populates the index is in the instructions in the dashboard.  The other one uses a |tstats query ( the _live version) and might not be suitable for larger environments.

These Splunk Dashboards use data gathered in one hour samplings, then runs an algorithm to present when a Z Score exceeds a configurable setting.

This dashhoard will present Z Scores for:
- The number of Hosts in each Sourcetype
- The number of Events in each Sourcetype
- The number of Events for each Host
- The number of Sourcetypes in each Index
- The number of Sourcetypes for each Host

Based on the data collected, this dashboard calculates the Z Score for each of those.  This provides a way to identifiy when a particular host, sourcetype or index deviates from its normal metric.  

Use:
-Create a new dashboard using the xml code provided.
-Open the "Details" (click on the line) and click the query link.  This will open a query in a new tab and run it.  Once you're comfortable with what you see, remove the comments from the entire "|collect" stanza at the bottom and save as a scheduled search (preferably once an hour).  This will collect the data into a Summary Index.
-This shoukd start to show results on the dashboard in a few hours.  

This process also provides historic data about hosts, sourcetyoes and indexes in your Splunk instance (through standard Splunk Query Language).


*A z-score, also known as a standard score, indicates how many standard deviations a data point is from the mean (average) of a data set.

A z-score allows for the comparison of data points from different distributions and helps to determine if a data point is typical or atypical within a given data set. A z-score of 0 indicates that the data point is exactly at the mean, positive z-scores indicate values above the mean, and negative z-scores indicate values below the mean.

For example, one log source generates around 1000 log entries per day, distributed across 5 different sourcetypes and 3 different indexes. If we were to lose 10 of these log entries, it might not be a significant issue, given the volume of logs produced.

However, consider different log source that only produces around 20 log entries per day. In this case, missing 10 log entries during a sampling period could represent a relatively larger concern, as it would correspond to a significant percentage of the total logs produced." 
