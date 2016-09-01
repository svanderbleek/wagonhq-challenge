## Problem 1: Streaming statistics computation

Wagon computes histograms, distributions, and other statistics on streaming query results. Given a stream of numbers and text, let’s calculate some stats!

Input

We’ve built a generator that outputs random web log data in CSV format. You can download it here:

Mac: https://s3.amazonaws.com/challenge.wagon/generator.zip
Linux: https://s3.amazonaws.com/challenge.wagon/generator-linux.zip
The CSV header includes column names and column types, like this:

"col1name (col1type)","col2name (col2type)",...

The generator takes in a number of rows you’d like returned as a command line argument:

./generator 10000

Consume and compute

Build an executable that consumes ~10000 rows from the generator and calculates the following basic statistics:

For all columns, compute:
count
null count
For number columns, compute:
minimum
maximum
average
For text columns, compute:
count(shortest value)
count(longest value)
average length
break ties alphabetically as needed
Spice it up

There are lots of fun ways to extend this — take it any direction that excites you! Here are a few ideas:

Some stats are harder to compute over streams. Try computing median or 95th percentile for number columns and distinct count for text columns.
The generator can also operate in “pull mode”: ./generator PULL
Run it like this and it will output a new row for every \n it receives on stdin/
Adjust your code to work with the generator in pull mode. How do you show progressive updates?
How does your code handle 1 million rows? 10 million? Measure memory or CPU performance, improve it, and show the difference.
If you love this, checkout these papers:

[HyperLogLog: the analysis of a near-optimal cardinality estimation algorithm](http://algo.inria.fr/flajolet/Publications/FlFuGaMe07.pdf)
[An Improved Data Stream Summary: The Count-Min Sketch and its Applications](https://7797b024-a-62cb3a1a-s-sites.googlegroups.com/site/countminsketch/cm-latin.pdf?attachauth=ANoY7cqqzULUs_j1G9mOlFjOo6__A5ezW-22UwYX1kIVdBOE6XQHHr_p_5oX9XHYaYr-kpEITleUobnKTjFCnfuvOxC9_Bx7C2BCuufAI_X7CLGpoRkKU6IjgXU9Cn4bThNnGmwt2NhnWO2_lV6L4Q95DOidllpVVMRDjmF5oWXSsTpYkp_vVgKMBG45ozCa5ccPB9oRZk22sx4PbchxN3g49cSZjW061A%3D%3D&attredirects=0)
[Why Bloom filters work the way they do](http://www.michaelnielsen.org/ddi/why-bloom-filters-work-the-way-they-do/)

## Problem 2: Interactive data display

We’re building a delightful user interface for analyzing data. Given a set rows and columns, let’s make a webpage to show it off—think nifty, read-only spreadsheet.

Input

Here’s a file of web-log data (1M rows): https://s3.amazonaws.com/challenge.wagon/input.csv

It’s in CSV format, with the column types in parentheses after the column names. For example,

"sessionId (id)","page (text)","latency (int)","timeOnPage (float)" b7af832e,explore,22,118.781 38f5841d,welcome,189,39.657 b90e8b3d,query,63,423.585 385b525c,query,180,332.658 386c25d4,,10,

Data on a page

Create a webpage with a table of the first 10K rows from the CSV.

Spice it up

Here are a few ideas, but welcome to get fancy!

Display all of the CSV’s data on the page and keep performance snappy.
Filter the table with a search box.
Make it usable on mobile.
Download our data generator (see above) and use it to show new data on every page load.
If you love this, you might also love these papers:

[7 Classic Foundational Vis Papers You Might not Want to Publicly Confess you Don’t Know](http://fellinlovewithdata.com/guides/7-classic-foundational-vis-papers)
[20 DataTable Examples with ReactJS](http://react.rocks/tag/DataTable)
[JavaScript Graph Comparison](http://www.jsgraphs.com/)
