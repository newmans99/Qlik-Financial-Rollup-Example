# Qlik Financial Rollup Example
This is an example implementation of a dynamic Chart of Accounts measure generator for Qlik Sense. You can modify the COA and the Data portions to connect to your data sources.

# Results
Leveraging your Chart of Accounts (or other Hierachy), you end up with a series of variables that can be leveraged in Master Items or directly in your visualzations. Using the example, you will can get the following output with a simple chart of accounts.

![Financial Example](https://github.com/newmans99/Qlik-Financial-Rollup-Example/raw/master/FinancialExample.png)

from the following Chart of Accounts:

|AccountCode|ParentCode|NodeName|Rollup|
|-----------|----------|--------|------|
|4010|4001|Product Sales|+|
|4020|4001|Services Sales|-|
|4030|4001|Training Sales|*|
|4115|4001|Website Sales|/|
|4202|4200|Sales Deductions Discounts|+|
|4204|4200|Sales Deductions Returns|+|
|4206|4200|Sales Deductions Promotions|~|
|5001|5000|Stuff|+|
|4001|4000|Gross Revenue|+|
|4200|4000|Sales Deductions|-|
|4000|0|Revenue|+|
|5000|0|Cost of Goods Sold|-|
|0||Gross Margin|


With variables getting created like:

```vExt_Gross_Margin = (+(+(((+SUM({$<Node={"4010"}>}Values)-1*SUM({$<Node={"4020"}>}Values))*(SUM({$<Node={"4030"}>}Values)))/(SUM({$<Node={"4115"}>}Values)))-1*(+SUM({$<Node={"4202"}>}Values)+SUM({$<Node={"4204"}>}Values)))-1*(+SUM({$<Node={"5001"}>}Values)))```



# Implementation
**For Qlik Sense Desktop:**
<ol>
<li>Download the [Financial Rollup Example.qvf](https://github.com/newmans99/Qlik-Financial-Rollup-Example/raw/master/Financial Rollup Example.qvf) file.
<li>Save the downloaded file to your "...\My Documents\Qlik\Apps" folder.
<li>From Qlik Sense Desktop Hub, open the "Financial Rollup Example" app and interact/review the Financial Rollup Example Sheet.
</ol>

**For Qlik Sense Server:**
<ol>
<li>Download the [Financial Rollup Example.qvf](https://github.com/newmans99/Qlik-Financial-Rollup-Example/raw/master/Financial Rollup Example.qvf) file.
<li>From QMC, upload the downlaoded app.
<li>From Qlik Sense Hub, open the "Financial Rollup Example" app and interact/review the Financial Rollup Example Sheet.
</ol>

# Application Load Script Logic Overview:
The load script has this basic flow...
<ol>
<li> Data Load - Bring in your data, key is that your data has a hiearchy of a Node, ParentNode, NodeName, and a Rollup Operator. The Data needs to have a Node and some type of Value or Amount column. Currently, the example app has an inline load, allowing for a transportable example.
<li>Transform - The logic here is to transform your hiearchy to understand the relationship between parent and children nodes.
<li>Create Variables - This section loops through all of the nodes, starting at the lowest (leaf) level, and working up the hiearchy. As it loops, it generates variables which can be used in your visualizations or in Master Items.
<li>Clean Up - Like all good Qlik Applications, you need to do a little clean up. Such as removing un-needed variables, dropping tables, and instructing the app to only allow certain columns for the application search capabilities.
</ol>

# Please help...
Please provide any comments or suggestions, specifically, I am looking for errors or problems in the load scriipt.

# Remaining items, I would like to add for future versions...
See Github Issues

# License
Released under the MIT license.
