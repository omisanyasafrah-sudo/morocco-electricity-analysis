# Exploratory Analysis of Morocco Electricity Consumption

AnalystLab Africa | Data Analytics Internship | Week 5
Prepared by Safrah Omisanya | Track: Data Analytics

## Project
An analysis of electricity consumption in three zones in Morocco, recorded every 10 minutes from 1 January to 30 December 2017 (52,416 readings), together with temperature, humidity, wind speed and two diffuse flow measurements. The project inspects and cleans the data, describes consumption patterns by hour, weekday, month and zone, tests how consumption is associated with weather, and gives recommendations for energy planning.

## Business questions answered
1. What patterns appear across the three zones?
2. Which hours and days are highest and lowest?
3. How does consumption vary across months?
4. Are temperature, humidity and wind speed associated with consumption?
5. Which zone is highest and lowest?
6. How can history support energy planning?

## Key findings
- Zone 1 is highest (average 32,345; 45.4% of the combined average), Zone 2 next (21,043), Zone 3 lowest (17,835) but the most variable.
- All zones peak at 20:00 and are lowest at 06:00 to 07:00. Zone 1 is about 89% higher at 20:00 than at 06:00.
- July and August are the busiest months. The highest reading was on 24 July at 20:10.
- Sundays are about 6% (Zone 1) and 12% (Zone 2) below weekday averages.
- Temperature has a moderate positive association with consumption (Spearman 0.38 to 0.44). Humidity looks negative but mostly reflects the daily cycle. Wind speed is weak.
- Zone 3 falls sharply after August. The data does not show why.

## Folder contents
| Item | Purpose |
|---|---|
| `electricity_analysis.ipynb` | Full analysis: inspection, cleaning, analysis, charts, findings |
| `powerconsumption_cleaned.csv` | Cleaned dataset with time columns and a Zone 3 high-reading flag |
| `Analytical_Report.pdf` | Short analytical report |
| `powerconsumption.csv` | Original dataset (input to the notebook) |
| `powerconsumption_datadictionary.csv` | Original data dictionary |
| `01_daily_trend.png`, `02_zone_comparison.png`, `03_hour_week_month.png`, `04_correlation_heatmap.png` | Charts |
| `05_daily_trend_interactive.html`, `06_temperature_scatter.html` | Interactive Plotly charts (download and open in a browser) |

## How to reproduce
1. Install Python 3.12 or 3.13 and tick "Add python.exe to PATH".
2. Open a command prompt in this folder and run:
   `pip install notebook pandas numpy matplotlib seaborn plotly`
3. Keep `powerconsumption.csv` and `powerconsumption_datadictionary.csv` in the same folder as the notebook (they are included in this repository). The notebook saves its charts into a `figures` folder, which it creates.
4. Run `jupyter notebook`, open `electricity_analysis.ipynb`, and choose Kernel > Restart Kernel and Run All Cells.

## Methodology
- **Inspection:** shape, types, missing values, duplicate rows and timestamps, 10-minute interval consistency, data dictionary review.
- **Cleaning:** Datetime converted from text; Year, Month, Day, Hour, DayOfWeek and Date columns added; unusual values investigated with the 1.5 x IQR rule, then flagged and kept.
- **Analysis:** group averages by zone, hour, weekday and month; busiest and quietest periods.
- **Environmental analysis:** Spearman and Pearson correlations, temperature bands, correlations after removing the average daily cycle, and correlations of daily averages.
- **Visualisation:** Matplotlib, Seaborn and Plotly.

## Assumptions
- The consumption values behave like power (kW) at the time of each reading, not energy used in the 10-minute interval, so averages and patterns are reported and readings are not summed into total energy. The data dictionary says kilowatt-hours, so this is an assumption the file cannot prove.
- GeneralDiffuseFlows and DiffuseFlows are described as emissions gases but behave like sunlight (about 0 at night, peak at midday). Their meaning is unclear and they are not used for conclusions.

## Limitations
- One year of data only, and 31 December is missing, so seasonality cannot be confirmed.
- Correlation is not causation: temperature, season and time of day move together.
- Zone locations and sizes are not provided.

## Individual work
Individual internship assignment, completed independently using the tools specified for the Data Analytics track.
