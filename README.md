# JSTOR-Wikidata-Project

Project developped for an interview at JSTOR Labs.

>>> Task: 
The Wikidata statistics page provides a top-level breakdown of Wikidata content.  
In the pie chart on that page you can see that over 40% of all items in Wikidata are an instance of “scholarly article”. 
Given the number of items in Wikidata as of today that probably equates to something like 23 million items.  
I’d like to better understand more about this scholarly article content.  
The assignment is to generate a profile of these ~23 million scholarly articles.  
Examples of interesting information to profile would include publication dates, publishers, journals, authors, topics, etc.  
This will require some creativity as the volume of this content will likely result in Wikidata query timeouts 
if the entire set of ~23 million items is targeted in a single query.  
The assignment work output should be recorded in Jupyter Notebooks (with python).  
The generated notebook(s) should include all Sparql queries used, any custom python code developed, 
and the resulting profile data in tabular and/or graphical visualizations.

>>> Development:
[See: https://drive.google.com/file/d/11RQd-b7T6KiRbtTjfiNhEBcvZoIYcYmS/view?usp=sharing]
- Selection of top 20 Wikipedias per scholarly articles
- Run 20 queries on Wikidata and download .csv files
- Import in Python
- Merge (fuzzy matching) and clean datasets  
- Statistical analysis and data visualizations
- time series review of language and publication years
- largest publisher per language
