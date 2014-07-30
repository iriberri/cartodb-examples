## Styling Torque maps in size and color

### Introduction

Usually, you can style your maps with CartoCSS in an easy way by using constraints with the actual value of your columns.

``#places_2[identifier="Sunny"] {
   marker-fill: #A6CEE3;
}``

Nevertheless, this is not how Torque works. 

When Torque library render points it does not render exactly the same points you have in the database, it aggregates the points in clusters in order to speedup rendering and data transfer.

So imagine you have this cartocss

``Map {
-torque-aggregation-function:"count(cartodb_id)";
-torque-resolution: 2;
}``

This implies that for the current zoom, Torque will fetch points in clusters of 2x2 pixels. Every cluster has a value, that value is calculated using `-torque-aggregation-function`, so in this case the value will be the number of points inside that cluster. That value can be accessed from CartoCSS using the variable `value`.

This means that Torque doesn't understand your string/numerical constraints, as it only knows about the variable `value`.

### How to adapt your data for Torque

Depending on your needs, you may need to build a new column (or a SQL query) that will allow you to differentiate your rows with respect to several columns in a unique variable.

#### Creating a variable to differentiate the data. 

#### Creating an aggregation function 

#### Building your constraints with CartoCSS 


*References:* 
https://github.com/CartoDB/torque/wiki/How-spatial-aggregation-works (by _@javisantana_)
