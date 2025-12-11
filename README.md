
<p align="center">
  <img src="https://github.com/user-attachments/assets/02f92943-66cf-40ff-a7d8-be7ae107e569" 
       alt="The Geography of Loss"
       width="880">
  <br>
</p>

<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/0/0a/Python.svg" width="55" />
  <img src="https://upload.wikimedia.org/wikipedia/commons/3/38/Jupyter_logo.svg" width="55" />
  <img src="https://upload.wikimedia.org/wikipedia/commons/3/3f/Git_icon.svg" width="55" />
  <img src="https://upload.wikimedia.org/wikipedia/commons/9/91/Octicons-mark-github.svg" width="55" />
  <img src="https://upload.wikimedia.org/wikipedia/commons/3/38/SQLite370.svg" width="55" />
</p>
<p align="center">
  <a href="#project-setup"><img src="https://github.com/user-attachments/assets/999d25d9-9bb8-4def-8385-773eed624f38" width="130"></a><a href="#data-sources-and-citations"><img src="https://github.com/user-attachments/assets/081188ed-9fa7-4e87-82e3-704d2fccbaa0" width="130"></a><a href="#analytical-questions"><img src="https://github.com/user-attachments/assets/d9013da1-4211-49f7-8bd1-88c05fee1729" width="130"></a><a href="#summary-of-approach"><img src="https://github.com/user-attachments/assets/0df784cc-fb57-4afc-89ce-d5987cf0c1cc" width="130"></a><a href="#acknowledgement-of-tools-and-assistance"><img src="https://github.com/user-attachments/assets/f8af1a0e-17ce-4a0d-86b0-c02d59c442b8" width="130"></a><a href="#special-acknowledgement"><img src="https://github.com/user-attachments/assets/e1c81def-63d1-4c3c-a9a9-dbe287eba13c" width="130"></a><a href="#next-steps"><img src="https://github.com/user-attachments/assets/8475e765-9093-466e-9403-d84b8facb3bd" width="130"></a>
</p>

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

```bash
python -m venv .venv
.venv\Scripts\Activate
```

Deactivate:

```
deactivate
```


#### macOS/Linux

```python3
-m venv .venv
source .venv/bin/activate
```

Deactivate
```
deactivate
```

### Install Dependencies

bash
```
pip install -r requirements.txt
```

### Run the Project

bash
```
jupyter lab
```
OR
```
jupyter notebook
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

One individual I held in mind during this work is Suzanne “Suzi” Roberts, a National Park Ranger and classmate from my first Wilderness EMT course. She died in 2004 while clearing fallen rocks from a road at Haleakalā National Park to protect visitors. Her story remains a reminder that every number in this dataset reflects a life rather than an abstraction.

This project aims to treat the dataset with accuracy, respect, and integrity.

You can read more about Ranger Roberts, written by some of the many people to whom she brought joy, at https://www.odmp.org/officer/reflections/17449-park-ranger-suzanne-e-suzi-roberts

## Next Steps

-Future improvements may include:
-Completing full exploratory data analysis
-Adding seasonal and environmental features
-Refining spatial visualizations and rate calculations
-Building interactive dashboards
-Updating schema as insights deepen

<p align="center">
  <img src="https://github.com/user-attachments/assets/a2eeca21-64fb-4834-9558-4162e2bd8be0" 
       alt="-----------------">
  <br>
</p>
