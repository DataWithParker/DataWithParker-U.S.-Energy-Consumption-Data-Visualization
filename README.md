# U.S.-Energy-Consumption-Data-Visualization

## Project Overview
This project presents a comprehensive data visualization poster analyzing the evolution of U.S. energy consumption from 1949 to 2024. Using federal energy datasets from the U.S. Energy Information Administration (EIA), the project illustrates long-term shifts in national fuel use, sector-level consumption patterns, and geographic variations across states.

The poster highlights the contrasting trajectories of major energy sources—showing the rapid decline of coal, continued reliance on petroleum and natural gas, and steady growth in renewable energy. These visual insights contextualize how economic cycles, federal energy policies, technological advances, and infrastructure changes have shaped the national energy landscape.

As of 2024, total U.S. primary energy consumption is 94 Quadrillion BTU, below the 2007 peak of 98.97 Quadrillion BTU. With growing demand from data centers, electrification, and semiconductor manufacturing, understanding these historical patterns is critical for forecasting future energy needs and informing energy policy decisions.

*This project was completed in R, with final layout and graphic refinement done in Adobe Illustrator.*

## Dataset Description

### Source  

All datasets used in this project come from the **U.S. Energy Information Administration (EIA)**.

### Structure  

- **Number of datasets:** 11  
- **Units used:**  
  - Quadrillion BTU  
  - Trillion BTU  
  - Billion BTU  
  - Million BTU  
- **National data range:** 1949–2024  
- **State-level data range:** 1960–2022  

### Key Variables  

- **Year** – primary time dimension used in all temporal analyses  
- **Energy Source** – e.g., coal, petroleum, natural gas, nuclear, solar, wind, biomass, hydroelectric  
- **Sector** – residential, commercial, industrial, transportation, electric power  
- **State** – used for geographic comparisons and mapping  

### Core Data Tables  

National-level:

- Primary energy **consumption by source**  
- Primary energy **production by source**  
- Sectoral energy consumption:  
  - Residential  
  - Commercial  
  - Industrial  
  - Transportation  
  - Electric Power  
- Summary tables combining total fossil, renewable, and primary energy usage  

State-level:

- Primary energy consumption by **source**, ranked by state  
- Total energy consumption per capita by **sector**, ranked by state  
- Total per capita energy consumption by state (used for mapping and regional rollups)  

---

## Methodology

This project integrates data cleaning, wrangling, aggregation, visualization, and design into a complete analytical pipeline.

### **Data Import & Cleaning**

National energy data were imported from multiple Excel tables (including primary energy consumption/production and sector-specific consumption), while state-level data were imported from ranked state tables.

**Key cleaning operations applied across all main datasets included:**

- Replacing `"Not Available"` text values with `0`  
- Converting character columns to numeric using a custom `clean_data()` function  
- Verifying data structures with `str()` and checking for missing values using `colSums(is.na())`  
- Ensuring consistent column naming and unit interpretation across tables  

A consistent cleaning function was used to process all datasets.

---

### **Data Transformation & Aggregation**

Data were transformed and aggregated to support the final visualizations and overall narrative of the poster.

**Fossil fuel aggregation:**  
- Combined coal, natural gas, and petroleum consumption by sector and time period  

**Renewable aggregation:**  
- Created a unified **Renewables** measure by summing hydroelectric, biomass, solar, wind, and geothermal consumption  

**Era grouping:**  
- Grouped years into the following periods for simplified flow visualizations:  
  - *1949–1970*  
  - *1970–1990*  
  - *1990–2010*  
  - *2010–2024*  

**Percent change calculations:**  
- Computed percentage change in fossil and renewable consumption between 1949 and 2023/2024 at both sector-level and national-level scales  

**Long-format reshaping:**  
Used `pivot_longer()` and `pivot_wider()` to prepare data for:  
- Stacked area charts  
- Line charts  
- Ridgeline plots  
- Lollipop charts  

**State-level processing:**  
- Extracted year-specific state values (e.g., 2022)  
- Joined state abbreviations with regions (Northeast, Midwest, South, West)  
- Summarized total energy consumption by census region  
- Identified top states by fuel type and by sector  

### Tools & Libraries  

The analysis and visualization were performed in **R**, using the following packages:ggplot2, readxl, tidyverse, readr, maps, dplyr, scales, packcircles, ggiraph, ggrepel, ggalluvial, RColorBrewer, ggridges, sf, paletteer, and usmap

## Poster
![Alt text](IST_719_Data_Viz_final_poster.jpg)


