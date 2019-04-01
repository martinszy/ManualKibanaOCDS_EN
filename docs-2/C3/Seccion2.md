# Discover

As its name implies, this section is just for a first data research. The search screen is divided into three main parts:
* Search engine  
* Fields mapping  
* Results space

!["Discover"](discover.png "Discover")

The main actions, both to search and configure the screen visualization are:
1. **Index Selector**: In the dropdown menu, different indexes imported into Kibana's instance can be found. Even some filters stick through indexes if there are matching fields.
2. **Search engine**: It allows us to ask a wide variety of questions about our database. To check that our query is working, there's a hit count just above the Search engine. The most common queries are:   

<table border=1>
    <tr>
        <th>Action</td>
        <th>Command</td>
        <th>Example</td>
    </tr>
    <tr>
        <td>Search in any field</td>
        <td>string</td>
        <td>México</td>
    </tr>
    <tr>
        <td>Search in specific field</td>
        <td>field:string</td>
        <td>buyer.name:México</td>
    </tr>
    <tr>
        <td>Search specific text in specific field</td>
        <td>field:"string"</td>
        <td>buyer.name:"Mexican Telecommunications"</td>
    </tr>
    <tr>
        <td>Search two texts in a field</td>
        <td>field:("string" OR "string")</td>
        <td>buyer.name:("Mexican Telecommunications" OR " Institute of Technology of Mexico")</td>
    </tr>
    <tr>
        <td>Search in two fields simultaneously</td>
        <td>field:"string" AND field:"string"</td>
        <td>buyer.name:"Mexican Telecommunications" AND tender.title:services</td>
    </tr>
    <tr>
        <td>Bigger or smaller</td>
        <td>field:>value</td>
        <td>contracts.value.amount:(>100000 AND <1000000)</td>
    </tr>
    <tr>
        <td>Wildcards, unknown values</td>
        <td>f?ield*</td>
        <td>M?xic*</td>
    </tr>
</table>

To know more options, you can review this documentation: [Query String Query](https://www.elastic.co/guide/en/elasticsearch/reference/6.x/query-dsl-query-string-query.html#query-string-syntax) and [Lucene Query Syntax](https://www.elastic.co/guide/en/kibana/6.x/lucene-query.html).

3. **Filters**: The graphical filters may do the same filter operations that we have just seen in the search engine, with the advantage that many filters can be easily added. [This tutorial](https://www.elastic.co/guide/en/elasticsearch/reference/6.x/query-filter-context.html) explains how filters can be edited to make them much more complex. If filters are applied on fields with strings, you will notice they are duplicated. One with the defined name, while the other ends in *.keyword*. We recommend using the second one. 

4. **Available fields**: The sidebar can be used to inspect the data header, show a first view of the data it contains and configure the results panel. 
    * _Configuration_: The wheel next to "Available Fields" displays a set of options to increase or decrease the fields you can see. In the case of non-tabular data, such as OCDS', it is advisable to unselect "Hide missing fields" in order to show the fields inside other fields. 
    * _Fields_: All the fields come together with a symbol to identify the sort of data they contain: the clock when it is temporary, pound sign to identify numbers, the "t" to identify texts or strings, a half dark sphere means it is a Boolean field, and the question mark means the field type is unknown (generally because it contains more fields). When you click a field, a graphic that maps the first 500 field values will be displayed. 
    * _Add_: The ADD button, which is highlighted by a red circle, can be used for the results panel to just show those selected values instead of showing the whole dataset. For example, we could use the `tender.numberOfTenderers` field, which shows the number of suppliers in each contracting process. Once we have it among the results, we can sort it to see which contracts have more contenders. 

5. **Save**: As mentioned at the beginning of the section, the visualizing option in the Discover section can be used to first explore, but once we got the desired results, we can save this search to graph it or send it to a dashboard. 
