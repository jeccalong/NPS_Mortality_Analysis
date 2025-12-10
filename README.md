# NPS Mortality Analysis

This project integrates multiple datasets related to U.S. National Park units—mortality incidents, visitation data, activities, amenities, park attributes, and geographic boundaries—to explore potential patterns contributing to visitor risk and safety. The primary focus of this project is data integration, cleaning, normalization, and preparation for meaningful analysis using Python, SQL, and geospatial tools.

---

## Project Setup

### 1. Clone the Repository

```bash
git clone https://github.com/jeccalong/NPS_Mortality_Analysis.git
cd NPS_Mortality_Analysis
```

### 2. Create and Activate a virtual environment.

#### Windows (PowerShell)

```python -m venv .venv
.venv\Scripts\Activate
```


Deactivate

```deactivate
```

#### macOS/Linux

```python3 -m venv .venv
source .venv/bin/activate
```

Deactivate
```deactivate
```

### Install Dependencies

bash
```pip install -r requirements.txt
```

### Run the Project

bash
```jupyter lab
```
OR
```jupyter notebook
```

Open the notebooks in the \Notebooks directory to run the analysis

## Data Sources and Citations

This project uses several publicly available datasets and API endpoints from the U.S. National Park Service.

#### Mortality Data
National Park Service Mortality Dashboard
https://www.nps.gov/aboutus/mortality-data.htm

#### Visitation Data
NPS Stats Reporting System (scraped + API)
https://irma.nps.gov/Stats/Reports/Park

#### Official Park Lists
FOIA Reading Room – Official NPS Park List
https://www.nps.gov/aboutus/foia/foia-reading-room.htm

#### NPS API Endpoints
Activities API: https://developer.nps.gov/api/v1/activities/parks
Amenities API: https://developer.nps.gov/api/v1/amenities

#### Geospatial Boundaries
NPS Administrative Boundaries (GeoJSON)
https://irma.nps.gov/DataStore/Reference/Profile/2224545?lnv=True

## Analytical Questions

This project is still in progress, but the primary analytical questions include:

How do recorded fatal incidents vary across National Park units when normalized for visitation volume?

Are there geographic or spatial patterns—across regions, physical landscapes, or boundaries—that relate to incident occurrence?

How do official park characteristics (designation, region, size, infrastructure level) relate to observed incident patterns?

Do certain activities, amenities, or park features correlate with particular categories or frequencies of mortality incidents?

What temporal patterns (month, year, season) appear within the mortality dataset, and how do they interact with visitation cycles?

## Summary of Approach

This project consolidates multiple NPS datasets with inconsistent naming conventions and identifiers. To support meaningful analysis, I created a unified key structure and designed a relational SQL schema connecting mortality data with:

-visitation statistics
-park metadata
-activities and amenities
-geographic boundaries
-historic or alternative park codes

Python was used for data cleaning, normalization, and integration. SQL stores the structured data, and geospatial and statistical libraries support further analysis and visualization.

Although analysis is ongoing, the integrated dataset and database structure form a solid foundation for identifying potential patterns in visitor safety.

## Acknowledgement of Tools and Assistance

This project was completed using Python, SQL, Jupyter notebooks, and standard data science libraries. ChatGPT and Claude were used for troubleshooting, code refinement, and support in generating reference tables. All final code, design decisions, and analysis were reviewed and implemented by me.

## Special Acknowledgement

While this work is technical, it also carries human significance. Each entry in the mortality dataset represents a real person, their community, and an event with lasting impact.

One individual I held in mind during this work is Suzanne “Suzi” Roberts, a National Park Ranger and classmate in my first Wilderness EMT course. She died in 2004 while clearing fallen rocks from a road at Haleakalā National Park to protect visitors. Her story remains a reminder that every number in this dataset reflects a life rather than an abstraction.

This project aims to treat the dataset with accuracy, respect, and integrity.

### Next Steps

-Future improvements may include:
-Completing full exploratory data analysis
-Adding seasonal and environmental features
-Refining spatial visualizations and rate calculations
-Building interactive dashboards
-Updating schema as insights deepen