<p align="center">
  <img src="https://github.com/user-attachments/assets/a2eeca21-64fb-4834-9558-4162e2bd8be0" 
       alt="-----------------">
  <br>
</p>

# The Geography of Loss
## ERD Reasoning

This ERD outlines the relational database schema for The Geography of Loss: A Data-Driven Exploration of Mortality and Risk in America's National Park Units. The schema was designed to bring together mortality incidents, park attributes, visitation statistics, and geospatial data from multiple National Park Service sources in a way that makes analysis practical and repeatable.

The schema uses a star-schema-inspired approach with fact tables, dimension tables, and dedicated structures for activities, amenities, and geospatial boundaries. The intention is to support both high-level statistical work and more exploratory, question-driven analysis.

## Core Design Principles
**Separation of Fact and Dimension Tables**

The database contains two primary fact tables

***Mortality Incidents*** – individual-level event data, including cause, intent, demographics, and date.

***Visits*** – monthly visitation counts for each park unit.

All categorical descriptors (such as intent, cause, activity, etc.) live in dimension tables so they can be joined cleanly and consistently.

## Dual Time Dimensions

Because mortality and visitation data are collected at different time grains, the schema uses two separate time dimensions.

***DATES*** (Daily):
Used for mortality analysis that depends on weekday/weekend patterns, seasons, and specific dates.

***MONTHS*** (Monthly):
Used for visitation data, which is only reported at the monthly level, and supports seasonal and year-over-year comparisons.

## Park & Geospatial Modeling
***Park Units***

The PARK_UNITS table stores identifiers and characteristics for each national park unit, including designation, region, and attributes like activities and amenities.

***Geospatial Boundaries***

The GEO table stores each park’s geometry and related shape metadata. This structure makes it easier to join boundaries with the cleaned geopandas DataFrame used for interactive mapping and spatial analysis in Folium.

## Activities and Amenities

Because parks can have many activities and many amenities, the schema uses bridge tables:

PARK_ACTIVITIES – many-to-many relationship between parks and activity types.

AMENITIES – stores amenity attributes linked to each park, with AMENITY_TYPES standardizing category names.

This structure allows analysis based on categories that may show meaningful insights in the relationship between park characteristics and mortality events.

## Analytical Advantages of This Design

The schema supports:

Trend analysis over time using either daily or monthly granularity

Mortality rate calculations normalized by visitor population

Regional comparisons

Activity and amenity based risk analysis

Geospatial visualizations