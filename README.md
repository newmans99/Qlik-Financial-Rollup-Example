# Qlik-Financial-Rollup-Example
This is an example implementation of a dynamic Chart of Accounts measure generator for Qlik Sense. You can modify the COA and the Data portions to connect to your data sources.


# Implementation
**For Qlik Sense Desktop:**
1. Download the [Financial Rollup Example.qvf](https://github.com/newmans99/Qlik-Financial-Rollup-Example/raw/master/Financial Rollup Example.qvf) file.
2. Save the downloaded file to your "...\My Documents\Qlik\Apps" folder.
3. From Qlik Sense Desktop Hub, open the "Financial Rollup Example" app and interact/review the Financial Rollup Example Sheet.

**For Qlik Sense Server:**
1. Download the [Financial Rollup Example.qvf](https://github.com/newmans99/Qlik-Financial-Rollup-Example/raw/master/Financial Rollup Example.qvf) file.
2. From QMC, upload the downlaoded app.
3. From Qlik Sense Hub, open the "Financial Rollup Example" app and interact/review the Financial Rollup Example Sheet.

# Application Load Script Logic Overview:
The load script has this basic flow...
1. Data Load
..Bring in your data, key is that your data has a hiearchy of a Node, ParentNode, NodeName, and a Rollup Operator. The Data needs to have a Node and some type of Value or Amount column.
2. Transform
..The logic here is to transform your hiearchy to understand the relationship between parent and children nodes.
3. Create Variables
..This section loops through all of the nodes, starting at the lowest (leaf) level, and working up the hiearchy. As it loops, it generates variables which can be used in your visualizations or in Master Items.
4. Clean Up
..Like all good Qlik Applications, you need to do a little clean up. Such as removing un-needed variables, dropping tables, and instructing the app to only allow certain columns for the application search capabilities.

# Please help...
Please provide any comments or suggestions, specifically, I am looking for errors or problems in the load scriipt.

# Remaining items, I would like to add for future versions...
See Github Issues

# License
Released under the MIT license.
