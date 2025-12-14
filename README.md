


<p align="center">
  <img src="assets/banner-geography-of-loss.png" 
       alt="The Geography of Loss"
       width="880">
  <br>
</p>

<p align="center"><a href="#project-setup"><img src="assets/nav-project-setup.png" width="130"></a><a href="#file-structure"><img src="assets/nav-file-structure.png" width="130"></a><a href="#data-sources-and-citations"><img src="assets/nav-data-sources.png" width="130"></a><a href="#analytical-questions"><img src="assets/nav-analytical-questions.png" width="130"></a><a href="#summary-of-approach"><img src="assets/nav-summary.png" width="130"></a><a href="#findings"><img src="assets/nav-findings.png" width="130"></a><a href="#acknowledgement-of-tools-and-assistance"><img src="assets/nav-tools.png" width="130"></a><a href="#special-acknowledgement"><img src="assets/nav-special-acknowledgement.png" width="130"></a><a href="#next-steps"><img src="assets/nav-next-steps.png" width="130"></a><a href="#license"><img src="assets/nav-license.png" width="130"></a></p>


**This project integrates multiple datasets related to U.S. National Park units, including mortality incidents, visitation data, activities, amenities, park attributes, and geographic boundaries, to explore potential patterns contributing to visitor risk and safety.** 

**The primary focus of this project is data integration, cleaning, normalization, and preparation for meaningful analysis using Python, SQL, and geospatial tools.**

---

<div align="center" style="display:flex; flex-wrap:wrap; justify-content:center; gap:8px;">

  <img alt="Python"     src="https://img.shields.io/badge/Python-3.x-022440?logo=python&logoColor=white" />
  <img alt="Pandas"     src="https://img.shields.io/badge/Pandas-Data%20Analysis-022440?logo=pandas&logoColor=white" />
  <img alt="NumPy"      src="https://img.shields.io/badge/NumPy-Numerical-022440?logo=numpy&logoColor=white" />
  <img alt="GeoPandas"  src="https://img.shields.io/badge/GeoPandas-Geospatial-022440?logo=geopandas&logoColor=white" />
  <img alt="Folium"     src="https://img.shields.io/badge/Folium-Interactive%20Maps-022440" />
  <img alt="Matplotlib" src="https://img.shields.io/badge/Matplotlib-Visualization-022440" />
  <img alt="SQLite"     src="https://img.shields.io/badge/SQLite-Database-022440?logo=sqlite&logoColor=white" />

</div>


---

## Project Setup

### 1. Clone the Repository

```bash
git clone https://github.com/jeccalong/NPS_Mortality_Analysis.git
cd NPS_Mortality_Analysis
```

### 2. Create and Activate a virtual environment

#### Windows (PowerShell)

```bash
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

Deactivate:

```bash
deactivate
```

---

#### macOS/Linux

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Deactivate:

```bash
deactivate
```

---

### Install Dependencies

```bash
pip install -r requirements.txt
```

---

### Run the Project

```bash
jupyter lab
```

or

```bash
jupyter notebook
```

Open the notebooks in the `notebooks/` directory to run the analysis.  
Run `acquisition_and_cleaning.ipynb` first, followed by `analysis.ipynb`.

<p align="center">
  <img src="assets/divider.png" 
       alt="-----------------">
  <br>
</p>

## File Structure

```text
NPS_Mortality_Analysis/
├── README.md
├── requirements.txt
├── .env.example
│
├── assets/                            # README navigation and visual assets
├── data/
│   ├── raw/                           # Original source data (unchanged)
│   │   ├── api/
│   │   ├── downloads/
│   │   └── scraped/
│   │
│   ├── processed/                     # Processed datasets / .gpkg files
│   │   └── nps_geo.gpkg
│   │
│   └── db/                            # SQLite database
│       └── nps_mortality_project.db
│
├── notebooks/
│   ├── acquisition_and_cleaning.ipynb # Run this notebook first
│   └── analysis.ipynb                 # Run this notebook second
│
├── maps/                               # Interactive .html map files
│   ├── mortality_rate_geo_choropleth.html
│   └── regional_mortality_rate_geo_choropleth.html
│
├── plots/                              # Static figures exported from analysis
│   ├── distribution_of_ages.png
│   ├── distribution_of_causes_pie_plot.png
│   ├── male_v_female_distribution.png
│   ├── mortality_rate_vs_number_of_activities.png
│   ├── spearman_correlation_activities.png
│   └── top20_barplot.png
│
└── erd/                                # Database structure + reasoning
    ├── erd.md
    ├── nps_erd.pdf
    └── nps_erd.png
```
<p align="center">
  <img src="assets/divider.png" 
       alt="-----------------">
  <br>
</p>

## Data Sources and Citations

This project uses several publicly available datasets and API endpoints from the U.S. National Park Service.

### Mortality Data
***Author***: National Park Service

***Description***: Official mortality dataset compiled by the NPS Office of Risk Management. Includes incident-level records of visitor and employee deaths across National Park units, as presented in the NPS Mortality Dashboard.

***Source***: https://www.nps.gov/aboutus/mortality-data.htm

### Visitation Data
***Author***: National Park Service

***Description***: Monthly and annual visitation statistics for all NPS units, maintained through the IRMA (Integrated Resource Management Applications) Stats Reporting System. Used to calculate relative risk, normalize mortality rates, and compare park usage over time.

***Source***: https://irma.nps.gov/Stats/Reports/Park

### Official Park Lists
***Author***: National Park Service

***Description***: The official list of all National Park System units, maintained in the NPS FOIA Reading Room. Includes designations, status, and authoritative park codes used to standardize and reconcile multiple datasets.

***Source***: https://www.nps.gov/aboutus/foia/foia-reading-room.htm

### NPS API Endpoints
***Author***: National Park Service

***Description***: Public REST API providing structured data on park activities, amenities, events, alerts, and more. Used in this project to retrieve activity lists and amenity data for each park unit.

***Source - Activities API***: https://developer.nps.gov/api/v1/activities/parks

***Source - Amenities API***: https://developer.nps.gov/api/v1/amenities

### Geospatial Boundaries
***Author***: National Park Service

***Description***: Administrative boundaries for all NPS units, provided as GeoJSON through the NPS IRMA DataStore. Used to generate maps, compute centroids, and spatially align park attributes.

***Source***: https://irma.nps.gov/DataStore/Reference/Profile/2224545?lnv=True

<p align="center">
  <img src="assets/divider.png" 
       alt="-----------------">
  <br>
</p>

## Analytical Questions

This project is still in progress and the questions guiding my work have evolved as I’ve explored the data. At this stage, the core questions I’m trying to answer include:

**How do recorded fatal incidents vary across National Park units once visitation volume is taken into account?**

I’m interested in whether normalizing incidents by visitor counts helps reveal meaningful differences between parks that would otherwise be hidden by raw numbers.

**Are there geographic or spatial patterns that help explain where fatalities occur?**

Generally speaking, terrain, weather patterns, and visitor profiles may be more similar when looking at geographic regions as opposed to system-wide. For example, both the situations you may encounter and the visitor profile vary wildly between park units such as the National Mall versus remote and harsh landscapes found in the Gates of the Arctic National Park.

**How do specific park characteristics like designation, region, infrastructure level, backcountry level, or emergency readiness, relate to mortality patterns?**

Part of this project is exploring whether certain types of parks carry different kinds of risk, as well as examining the public safety benefits that may come from more resourced parks with similar terrain and features when compared to less resourced parks.

**Do the activities a park offers correlate with its overall mortality rate or with certain categories of incidents?**

Are some activities inherently more dangerous across all locations, or do some parks appear more successful at mitigating the risks associated with specific activities?

**What temporal patterns show up in the mortality data, and how do they interact with visitation cycles?**

It seems straightforward that seasonal patterns would create more dangerous conditions, but does this result in increased mortality or does the visitor profile change in a way that actually reduces mortality as casual visitors and those unprepared for the conditions may not be common in more harsh conditions.

<p align="center">
  <img src="assets/divider.png" 
       alt="-----------------">
  <br>
</p>

## Summary of Approach

This project brings together several NPS datasets that were never designed to work together, each with its own identifiers, naming conventions, and structural quirks. One of my first major tasks was creating a unified key system and a relational SQL schema that connects visitation statistics, activities, amenities, geospatial boundaries, multiple inconsistent park codes and naming conventions, and individual mortality records.

Python was used for cleaning, normalization, and integration. I standardized codes, resolved mismatches, and prepared the data, which was then loaded into a SQL database.

Once the dataset was stable, I began applying statistical techniques to understand patterns more clearly. Techniques utilized include:

***Z-score standardization***

Used to identify parks that meaningfully differ from the overall mortality distribution and to place parks on a comparable scale. This was used as an initial step to determine what variances exist and formulate the next steps for developing a system to analyze mortality rates that could be both factually accurate and statistically meaningful.

***Empirical Bayes credibility adjustment***

This is the method used to stabilize park-level mortality rates and create credible rates used for comparison. Small units, units with very low visitation, and units with very few incidents can show unstable raw rates. The empirical Bayes approach "shrinks" extreme values toward the system-wide mean in a controlled and consistent way. Parks with more data retain more of their raw rate information and parks with sparse data receive more adjustment. This produces far more reliable comparisons across units.

***Decile grouping and mapping***

Mortality rates were binned into percentile groups to support choropleth visualization and make relative differences intuitive on a map.

***Variance comparisons***

During analysis, I hypothesized that the variance in mortality rates would be more stable when analyzed regionally vs system-wide. I compared the variance of mortality rates across the entire National Park System to the variance within each individual region. The goal was to see whether parks inside the same region showed more consistency. I used these to test whether regional grouping explained differences in mortality. My hypothesis did not hold, which helped clarify the direction of the analysis.

***Spearman Correlation***

I converted the raw activities data, a single long list of all activities offered at each park, into a binary matrix showing whether each activity was present or not. Then I used Spearman correlation to look for consistent upward or downward trends between these activity indicators and mortality rates.

The project is still ongoing, but the standardized schema, unified keys, and initial round of statistical work—including the credibility-adjusted rates—provide a strong foundation for deeper spatial, temporal, and multivariate analysis as I continue developing the project.

<p align="center">
  <img src="assets/divider.png" 
       alt="-----------------">
  <br>
</p>

## Findings

This project is still in progress, but several clear patterns have been observed.

***Mortality rates vary substantially across park units.***

After adjusting for visitation volume—using an empirical Bayes credibility approach to stabilize the rates—parks still differ widely in mortality risk. This confirms that meaningful variation exists at the park level, not just as an artifact of visitation counts.

***Mapping reveals meaningful spatial variation at the park level.***

Park-level choropleth mapping with a continuous gradient based on credible mortality rates shows clear variation across the National Park System.

***Regional grouping does not explain differences in mortality.***

While mapping appears to identify strong regional patterns in mortality rates, comparing the variance of mortality rates system-wide to the variance within each NPS region, revealed regional variances just as large or larger. This means that parks within the same region are not more similar to each other in terms of mortality risk, so region alone isn’t a useful explanatory factor.

***Park-offered activities do not show strong relationships with mortality rates.***

After using Spearman correlation to explore potential relationships, it became apparent that most correlations were weak and none suggested that a single activity meaningfully raises or lowers risk at the park level. It was observed that activities that are associated with remoteness may be associated with higher mortality.

**Parks offering more activities tend to have lower mortality rates overall.**

When exploring the total number of activities offered per park, I found a slight trend that validates the remoteness finding revealed by Spearman correlation analysis. Parks with more recreational offerings generally had lower mortality rates. The relationship isn’t strong, but it’s consistent enough to note and may indicate that the strongest factor in preventing mortality is infrastructure, which speaks to the delicate balance of leaving our wild places wild, while all making them safe and accessible to visitors. 

<p align="center">
  <img src="assets/divider.png" 
       alt="-----------------">
  <br>
</p>

## Acknowledgement of Tools and Assistance

This project was developed using ***Python***, ***SQL***, and ***Jupyter notebooks***, along with common data science libraries including ***pandas***, ***NumPy***, ***GeoPandas***, ***Folium***, and ***Matplotlib***. ***SQLite*** was used to design and manage the relational database that supports the analysis.

AI tools including ***ChatGPT*** and ***Claude*** were used for troubleshooting, code refinement, debugging assistance, and help generating reference tables or lookup structures when needed. All final code, methodological choices, interpretations, and analytical decisions were reviewed, validated, and implemented by me.

Tools and properly licensed stock images from the ***Adobe Creative Suite*** were used to develop a unified color palette and imagery for this project.

<p align="center">
  <img src="assets/divider.png" 
       alt="-----------------">
  <br>
</p>


## Special Acknowledgement

While this work is technical, it also carries human significance. Each entry in the mortality dataset represents a real person, their community, and an event with lasting impact.

One individual I held in mind during this work is Suzanne “Sooz” Roberts, a National Park Ranger and classmate from my first Wilderness EMT course. She died in 2004 while clearing fallen rocks from a road at Haleakalā National Park to protect visitors. Her story remains a reminder that every number in this dataset reflects a life rather than an abstraction.

This project aims to treat the dataset with accuracy, respect, and integrity.

You can read more about Ranger Roberts, written by some of the many people to whom she brought joy, at https://www.odmp.org/officer/reflections/17449-park-ranger-suzanne-e-suzi-roberts

<p align="center">
  <img src="assets/divider.png" 
       alt="-----------------">
  <br>
</p>


## Next Steps

This project has already shown that park-level mortality varies in meaningful ways, and that building a unified analytical structure makes those patterns easier to see. 

By normalizing incidents for visitation, applying an empirical Bayes credibility adjustment, and creating a consistent relational database, I’ve been able to move beyond raw counts and uncover relationships that weren't visible in the original datasets. 

This work is important because identifying where and how fatal incidents occur can support better risk communication, visitor safety planning, and resource allocation across the National Park System, and also be used to develop safety insights and recommendations for wilderness areas that don't have the benefit of large amounts of data, such as state and regional park systems and independently held conservation areas. 

Looking ahead, several next steps will continue to develop the analysis:

***Complete full exploratory data analysis (EDA) to better understand system-wide distributions and relationships.***

***Expand temporal analysis to incorporate seasonal and multi-year trends, including effects of the COVID-19 pandemic on visitation and risk.***

***Test additional statistical models to strengthen and validate rate calculations.***

***Build interactive dashboards for more intuitive and accessible exploration of park-level patterns.***


<p align="center">
  <img src="assets/divider.png" 
       alt="-----------------">
  <br>
</p>

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

This license applies to original code, analysis, and documentation in this repository. Source datasets are governed by their respective providers.
