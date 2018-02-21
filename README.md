# SympluR
R package for analyzing data from the Healthcare Social Graph via access to the Symplur API.

## Get started
To install R package from GitHub:
```
library("devtools")
install_github('symplur/SympluR')
library(SympluR)
```

## Symplur API Credentials
To make us of the R package you need to have access to the Symplur API. Please [contact Symplur](https://www.symplur.com/contact/) if you want to gain access.

You need the `clientId` and the `clientSecret` provided to you by Symplur. The R package will prompt you for this information during the first API call in your session. Paste in your credentials when asked.

## Documentation
Find the documentation in R for each function in this package. Example:

`?symplurSummary`

To learn more about each Symplur API endpoint used in this package and the accepted parameters please see the [Symplur API Documentation](https://api.symplur.com/v1/docs).

## Example Usage
### Summary

This will create a list `LCSM` with statistics of the database and the time period selected. The stats include tweets, mentions, impressions, users, retweets, replies, urls_shared, etc.

`LCSM <- symplurSummary("09/01/2017", "09/08/2017", list("databases[]" = "#LCSMDemoData"))`

### Summary Table
This will create a data frame with summary statistics of all databases and time periods defined in an existing data frame `LCSMquery`.
First create in a spreadsheet columns 'database', 'start' and 'end'. Add rows according to your need. Then export as CSV-file. Example table:

| database      | start      | end        |
|---------------|------------|------------|
| #LCSMDemoData | 09/01/2017 | 09/06/2017 |
| #LCSMDemoData | 09/06/2017 | 09/13/2017 |
| #LCSMDemoData | 09/13/2017 | 09/19/2017 |

Load that CSV into R as a data frame:

`library(readr)`

`LCSMquery <- read_csv(file.choose())`

Then finally run the analysis:

`LCSManalysis <- symplurSummaryTable(LCSMquery)`
