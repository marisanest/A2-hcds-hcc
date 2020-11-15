# A2-hcds-hcc


The goal of this project is to acquisit, process, analyze, and publish a data set of the monthly traffic on Wikipedia. 


## Data source

As data source the Wikimedia Foundation REST API is used. Terms and Conditions to the Wikimedia Foundation REST API can be found here:
[Terms and Conditions][1]. The content accessed via this API is licensed under the [CC-BY-SA 3.0][2] and [GFDL][3] licenses, and thus all produced data throughout this project follows the same licensing policy.

To get a comprehensive set of data to different APIs need to be called:

1. The **Legacy Pagecounts API** ([documentation][4], [endpoint][5]) provides access to desktop and mobile traffic data from December 2007 through July 2016.
2. The **Pageviews API** ([documentation][6], [endpoint][7]) provides access to desktop, mobile web, and mobile app traffic data from July 2015 through last month.


## Results


The resulting `CSV`-formatted data file `en-wikipedia_traffic_200712-202010.csv` can be found in the folder `clean_data`. It contains the following fields:

| name | description |
|-------------------|-------------------|
| year | Year with the format YYYY |
| month | Month with the format MM |
| pagecount_all_views | Desktop and mobile views in the specific period fetched vie the Pagecounts API |
| pagecount_desktop_views | Desktop views in the specific period fetched vie the Pagecounts API |
| pagecount_mobile_views | Mobile views in the specific period fetched vie the Pagecounts API |
| pageview_all_views | Desktop and mobile views in the specific period fetched vie the Pageviews API |
| pageview_desktop_views | Desktop views in the specific period fetched vie the Pageviews API |
| pageview_mobile_views | Mobile views in the specific period fetched vie the Pageviews API |

    
## Known issues & special considerations

### Wikimedia Foundation REST APIs

The use of two different data sources leads to differences in the data represented by the two sources. For example the Pageview API excludes spiders/crawlers, while data from the Pagecounts API does not. As a result, the two data sources may provide different values, even if the same period is considered. The two data sources also overlap, so that for the period from July 2015 to July 2016 both sources provide data about the monthly traffic on Wikipedia. 
    

## Getting started


### Prerequisites

In order to use this project (espaccilay the jupyter note book), please ensure that you have a Python version greater or equal to `3.6.1`, a working installation of [Poetry][8] and [git][9] installed.


### Setup

1. Clone this repository (or use SSH) and move it into the repo root.

    git clone https://github.com/marisanest/A2-hcds-hcc.git
    cd A2-hcds-hcc

1. Install the dependencies in the repo root.

    poetry install

1. Create a subshell within the virtual environment by running:

    poetry shell

1. Open the project with Jupyter in your browser.

    jupyter notebook
    

----

[1]:https://www.mediawiki.org/wiki/Wikimedia_REST_API#Terms_and_conditions   
[2]:https://creativecommons.org/licenses/by-sa/3.0/
[3]:https://www.gnu.org/copyleft/fdl.html
[4]:https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts
[5]:https://wikimedia.org/api/rest_v1/#!/Pagecounts_data_(legacy)/get_metrics_legacy_pagecounts_aggregate_project_access_site_granularity_start_end
[6]:https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews
[7]:https://wikimedia.org/api/rest_v1/#!/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end
[8]:https://python-poetry.org/docs/
[9]:https://git-scm.com/book/en/v2/Getting-Started-Installing-Git
