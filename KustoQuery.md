# Kusto Query Cheat Sheet 

Kusto Query Cheat Sheet for learning KQL (Kusto Query Language) from Scratch. Kusto can be used in Azure Monitor Logs, Application Insights, Time Series Insights and Defender Advanced Threat Perception.

Kusto Query Language (KQL) is a read-only query language, whoch processes the data and retunrs the results.
It is very similar to SQL with a sequence of statements are modeleded as a flow of tabular data output from
the previous statement to the next statement. These statements are concatenated with a pipe (|) character.
In KQL, the query starts with the table name followed by the pipe character after which the conditions are defined.
KQL is the query language and the Kusto Engine is the enginge that receives the queries in KQL to execute them.


**Useful learning resources**
* [Get started with Azure monitor](https://docs.microsoft.com/en-us/azure/azure-monitor/log-query/get-started-portal)
* ...

**Content**
- [Kusto Query Cheat Sheet](#Kusto-Query-Cheat-Sheet)

## Searching

Search for a specific String across all datasets
```kusto
search "FLORIDA" 
| take 5
```

The `take` command limits the output of the search to a number of 5 results. This spees up the query.
Kusto Queries can query a long time if the database is large. To avoid long running queries
the take command can be used before running the query.

Search for a specific String in a single dataset
```kusto
StormEvents 
| search "FLORIDA"
```

Search for a specific String in multiple, specific datasets
```kusto
search in (Covid19,StormEvents) "FLORIDA"
| take 5
```

Search for a match for a specific column
```kusto
StormEvents
| search State == "FLORIDA"
| take 5
```

Search for a term anywhere in text
```kusto
StormEvents
| search "*FLOR*"
| take 10
```

Searching for columns that begins with
```kusto
StormEvents
| search * startswith "FORI"
| take 5
```

Searching for columns that begins with
```kusto
StormEvents
| search * endswith "RIDA"
| take 5
```

Search starts and ends with a specific term, anything in between variable
```kusto
StormEvents
| search "FL*DA"
| take 5
```

** Combining searches **
