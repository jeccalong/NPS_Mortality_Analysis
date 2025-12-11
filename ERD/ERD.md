<p align="center">
  <img src="https://github.com/user-attachments/assets/a2eeca21-64fb-4834-9558-4162e2bd8be0" 
       alt="-----------------">
  <br>
</p>

# The Geography of Loss
## ERD Reasoning

This ERD outlines the relational database schema for The Geography of Loss: A Data-Driven Exploration of Mortality and Risk in America's National Park Units. The schema was designed to bring together mortality incidents, park attributes, visitation statistics, and geospatial data from multiple National Park Service sources in a way that makes analysis practical and repeatable.

The schema uses a star-schema-inspired approach with fact tables, dimension tables, and dedicated structures for activities, amenities, and geospatial boundaries. The intention is to support both high-level statistical work and more exploratory, question-driven analysis.

## Analytical Advantages of This Design

The schema supports:

Trend analysis over time using either daily or monthly granularity

Mortality rate calculations normalized by visitor population

Regional comparisons

Activity and amenity based risk analysis

Geospatial visualizations

## Schema Outline

**Fact Tables**

- **MORTALITY_INCIDENTS**  
  One row per mortality event.  
  Key fields: `incident_id` (PK), `park_id`, `date_id`, `cause_id`, `intent_id`, `sex_id`, `age_range_id`, `activity_id`, `incident_date`.

- **VISITS**  
  Monthly visitation counts by park. One row per month for each park.
  Key fields: `visits_id` (PK), `park_id`, `month_id`, `recreation_visitors`, `nonrecreation_visitors`, `total_visitors`.

**Time Dimensions**

- **DATES**  
  Daily time dimension for incident-level analysis.  
  Key fields: `date_id` (PK), `calendar_date`, `year`, `month`, `day`, `day_of_week`, `is_weekend`, `season`.

- **MONTHS**  
  Monthly time dimension for visitation and seasonal trends.  
  Key fields: `month_id` (PK), `year`, `month_number`, `month_name`, `season`.

**Park & Location Dimensions**

- **PARK_UNITS**  
  Canonical list of park units.  
  Key fields: `park_id` (PK), `key_code`, `park_name`, `designation`, `region`, `infrastructure_level`, `backcountry_level`, `emergency_readiness`.

- **GEO**  
  Geospatial boundaries and geometry for each park.  
  Key fields: `geo_id` (PK), `park_id`, `geometry`, `shape_area`, `shape_leng`.

**Categorical Dimensions**

- **CAUSE_TYPES**  
  Standardized cause-of-death groupings.  
  Key fields: `cause_id` (PK), `cause_name`, `cause_group`.

- **INTENT_TYPES**  
  Standardized intent categories.  
  Key fields: `intent_id` (PK), `intent_name`.

- **SEX**  
  Reported sex categories.  
  Key fields: `sex_id` (PK), `sex_label`.

- **AGE_RANGES**  
  Age bands used in reporting.  
  Key fields: `age_range_id` (PK), `age_range_label`.

- **ACTIVITY_TYPES**  
  Standardized activity categories.  
  Key fields: `activity_id` (PK), `activity_name`.

- **AMENITY_TYPES**  
  Standardized amenity categories.  
  Key fields: `amenity_type_id` (PK), `amenity_type_name`.

**Bridge Tables**

- **PARK_ACTIVITIES**  
  Links parks to the activities they offer (many-to-many).  
  Key fields: `park_activity_id` (PK), `park_id`, `activity_id`.

- **AMENITIES**  
  Links parks to amenities and their types.  
  Key fields: `amenity_id` (PK), `park_id`, `amenity_type_id`, `amenity_description`.
