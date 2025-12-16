# UCLA Law CBBDP Custodial Mortality Project Data

> <https://uclaprisondata.org/>

## Purpose of Data Collection

To better monitor the public health conditions behind bars, the project began gathering data on all-cause deaths in U.S. prisons in June 2020. Because prison agencies report different records on deaths in custody, the project has attempted to standardize records into similar variables so the public can compare what information agencies make available and study the data they do release.

The project intends this repository to function as a tool for the public and researchers to better understand the drivers of deaths in custody and assist policymakers in developing strategies to reduce their occurence. In particular, the project hopes this database helps support the full implementation of the Death in Custody Reporting Act [(link to bill)](https://www.congress.gov/bill/113th-congress/house-bill/1447/text) by supplementing 'Mortality in Correctional Institutions' reports, which were produced by the U.S. Department of Justice up until 2019, and assisting efforts to study (1) how this data may be used to reduce the number of deaths in custody, and (2) how carceral facility management practices may contribute to deaths in custody.

## Accessing the Data (2019-2024)

As of December 16, 2025, this repository incorporates custodial mortality data through 2024.

**National aggregate data by state (2019–2024):** [prison_agency_counts.csv](https://github.com/uclalawcovid19behindbars/custodial_mortality_project/blob/main/Data/Output/prison_agency_counts_2019_2024.csv)

**Individual-level death records by state:** [Raw Deaths folder](https://github.com/uclalawcovid19behindbars/custodial_mortality_project/tree/main/Data/Raw/Prison_Deaths/State_Reported_Deaths)

These datasets expand upon prior 2019–2021 data, adding standardized counts and individual records for 2022, 2023, and 2024. Data from the Bureau of Prisons and all 50 state prison systems have been integrated where available.

## How to Navigate This Repository

-   Start in **Data/** if you are looking for the actual death records and counts.
-   Use **Data/Raw/** to view individual-level files received from states or agencies. Missingness varies across states.
-   Check **Data/Aggregated_by_State/** for state-level totals that are ready to use.
-   Look in **Data/External/** for supporting datasets used for validation or context.
-   Open **Crosswalks/** to see how facility names and IDs were standardized across states.
-   Go to **Documents/** for state-by-state source guides and example records.
-   Each state folder in **Documents/** includes a short **source guide** and **example files** showing what the data looks like.

# Methodology

## Data Collection Procedures

Data on deaths in prisons and prison demographics comes from a variety of sources. Where prison death data is listed publicly on an agency website or where another organization has already collected and processed records on deaths in custody for a particular agency, the project has gathered, standardized, and reproduced those records here.

Examples of U.S. prison agencies that publicly list records on deaths in custody include the Arizona Department of Corrections [(link to source)](https://corrections.az.gov/inmate-death-notifications) and the Florida Department of Corrections [(link to source)](http://www.dc.state.fl.us/pub/mortality/index.html). The project has reproduced records from the Texas Justice Initiative for deaths in Texas state prisons, Incarceration Transparency at Loyola University New Orleans, College of Law for deaths in Louisiana state prisons, and the NPR Investigations team for deaths in Bureau of Prisons facilities.

Where information on deaths in prisons was not publicly available through an agency or another organization, or was not provided at the individual or facility-level, the project used public records requests to gather records on deaths in custody and standardized these records into a uniform database. For each request, the project asked for records from 2015 to 2020 and for the following pieces of information for each death:

-   Name of individual;
-   Age, race, and sex of individual;
-   Date of death;
-   Facility to which individual was assigned;
-   Location of death (e.g., cell number or hospital name);
-   Type of death (e.g., suicide, homicide, accident, drugs/alcohol, illness, other);
-   Additional details about death including circumstances, cause of death, and/or details of illness (if illness is listed as type of death).

### Potential Death Variables

| Variable | Description |
|--------------------|----------------------------------------------------|
| `State` | State prison system |
| `Year` | Year of death(s) |
| `Month` | Month of death(s) |
| `Death.Date` | Date of death(s) |
| `Facility` | Facility of death(s) |
| `CMP.ID` | Facility ID in project data [COVID Data](https://github.com/uclalawcovid19behindbars/data) |
| `Full.Name` | Full name of decedent |
| `Last.Name` | Last name of decedent |
| `First.Name` | First name of decedent |
| `ID.No` | Agency-assigned ID number of decedent |
| `Sex` | Sex of decedent |
| `Gender` | Gender of decedent |
| `Race` | Race of decedent |
| `Ethnicity` | Agency-listed ethnicity |
| `DoB` | Date of birth of decedent |
| `DoB.Year` | Year of birth of decedent |
| `Death.Age` | Age at death of decedent |
| `Circumstance.General` | General circumstances of death (N.B. not necessarily cause of death) |
| `Circumstance.Specific` | Specific circumstances of death (N.B. not necessarily cause of death) |
| `Circumstance.Other` | Other circumstances of death (N.B. not necessarily cause of death) |
| `Location` | Specific/other listed location of death |
| `Total.Deaths` | For aggregated categories, the total number of deaths |

### Context Notes on Potential Death Variables

The project only reproduces records provided to it and other projects. The project does not correct or investigate records for accuracy aside from data 
validation efforts to ensure total counts of deaths match or are similar to reporting for that agency produced by the Bureau of Justice Statistics. 
As such, there may be errors or issues with information contained within these variables. 
In particular, circumstances of death were reported differently across prison agencies and do not always reflect actual causes of death. 
Many death records are labeled as 'Natural' and 'Undetermined,' which provide little detail on the circumstances of death. For more context on issues with 
custodial death investigations please see the following resources.

> Nick Shapiro, Terrence Keel. *Natural Causes? 58 Autopsies Prove Otherwise*. UCLA Carceral Ecologies Lab, <https://ucla.app.box.com/s/sv54jmxhmq19kqifpakh4jfu3vnmhbqt/file/974263270262>

> Roger Mitchell Jr., Jay Aronson. *Death in Custody: How America Ignores the Truth and What We Can Do About It*. Johns Hopkins University Press, <https://www.press.jhu.edu/books/title/12925/death-custody>

### Documents

This folder contains documentation for how the project obtained data for each state prison system. 
Sub-folders for each state contain a R Markdown file describing how it obtained the data, what variables are present in the data, 
and how to load and compare annual aggregates from the data with past MCI reports from BJS.

`Example` folders contain raw unprocessed versions of the documents / data sources used to create the datasets in the `Raw` folder.

### External Data

| Dataset | Source | Description |
|------------------|-----------------------|-------------------------------|
| `msfp0119stt14.csv` | BJS, MCI Reports (2000-2019) | Totals of deaths of state and federal prisoners (unprocessed) |
| `msfp0119stt14_cleaned.csv` | BJS, MCI Reports (2000-2019) | Same as above, processed for easy loading and comparison |
| `p20stt09.csv` | BJS, NPS Reports (2019-2020) | Releases of state and federal sentenced prisoners (unprocessed) |
| `p222stt09.csv` | BJS, NPS Reports (2022-2023) | Releases of state and federal sentenced prisoners (unprocessed) |
| `p20stt09_cleaned.csv` | BJS, NPS Reports (2019-2020) | Same as above, processed for easy loading and comparison |
| `vera_pjp_s2021_appendix.csv` | Vera, People in Prisons and Jails Spr 2021 | Counts of state and federal prisoners |
| `hifld_prison_boundaries_2022.csv` | DHS, HIFLD Prison Boundaries Data | DHS ensus of carceral facilities conducted |

## Citations

For most states, data in this repository were obtained **directly from state Departments of Corrections (DOCs)** through public records requests or direct agency sharing. 
In some cases, states publish custodial death data publicly or through legislative, oversight, or research organizations; in those instances, publicly available data were used and standardized for inclusion here.

Because several states and federal agencies require attribution when their data are reused, users must also cite the **original source** listed below when using data from those jurisdictions.

------------------------------------------------------------------------

### Alabama
Alabama Department of Corrections. (2021). *Code of Alabama §14-1-24—Monthly reports (Fiscal Year 2021).*  
Research and Planning Division, Joint Legislative Prison Oversight Committee.  
https://doc.alabama.gov/statreports.aspx

Alabama Department of Corrections. (2022–2025). *Code of Alabama §14-1-24—Quarterly reports (Fiscal Years 2022–2025).*  
Research and Planning Division, Joint Legislative Prison Oversight Committee.  
https://doc.alabama.gov/statreports.aspx

### Florida
Florida Department of Corrections. (2025). *Inmate mortality statistics.*  
https://www.fdc.myflorida.com/statistics-and-publications/inmate-mortality#mortality_graph

### Hawaii
Hawaii Correctional System Oversight Commission. (2025). *Hawaii correctional system mortality data (2019–2024).*  
235 S. Beretania Street, 16th Floor, Honolulu, HI 96813.

### Louisiana
Armstrong, A., Mitchell, J., Navalance, E., & Farris, S. (n.d.).  
*Incarceration transparency: Louisiana deaths behind bars.*  
Loyola University New Orleans, College of Law.  
https://www.incarcerationtransparency.org/

### Minnesota
Minnesota Department of Corrections.  
*Health & safety in correctional facilities: Legislative reports.*

- 2022 report:  
  https://mn.gov/doc/assets/2022%20Health%20and%20Safety%20in%20Correctional%20Facilities_tcm1089-565603.pdf
- 2023 report:  
  https://mn.gov/doc/assets/2023%20Health%20and%20Safety%20in%20Correctional%20Facilities_tcm1089-609949.pdf
- 2024 report:  
  https://www.lrl.mn.gov/docs/2025/mandated/250306.pdf

### Missouri 
Scott, I. (2025, December 12). *Missouri prison system comprehensive death data release: How to access the state prison death dataset*. 
The Marshall Project. https://www.themarshallproject.org/2025/12/12/missouri-state-prison-death-data-access

### New York
Correctional Association of New York. (n.d.).  
*Deaths in custody dashboard.*  
https://www.correctionalassociation.org/data/dashboard-deaths-in-custody

### Ohio
Harland, A. (2022). *Ohio deaths in custody – 2022.*  
Ohio Office of Criminal Justice Services.  
https://ocjs.ohio.gov

### Tennessee
Tennessee Department of Correction.  
*Statistical abstracts.*

- Fiscal Year 2020–2021:  
  https://www.tn.gov/correction/statistics/annual-reports.html
- Fiscal Year 2021–2022:  
  https://www.tn.gov/correction/statistics/annual-reports.html

### Texas
Texas Justice Initiative. (2022–2024).  
*Deaths in custody dataset* [Data set].  
https://www.texasjusticeinitiative.org

### Virginia
Virginia Department of Criminal Justice Services. (2025, July).  
*Virginia civilian deaths in custody in 2024.*  
Commonwealth of Virginia.  
https://www.dcjs.virginia.gov

### Washington
Washington State Department of Corrections. (2025, October).  
*Death statistics for DOC incarcerated individuals.*  
https://doc.wa.gov/corrections/services/health-services

------------------------------------------------------------------------

If you use any of the **prison population data** in this repository from the **Vera Institute of Justice**, please also cite their reporting.

> Jacob Kang-Brown, Chase Montagnet, Jasmine Heiss.\
> *Vera Institute of Justice: People in Jail and Prison in Spring 2021.*\
> <https://www.vera.org/publications/people-in-jail-and-prison-in-spring-2021#>:\~:text=By%20spring%202021%2C%20jail%20populations,reduce%20incarceration%20through%20spring%202021

If you use any of the **execution data** in this repository from the **Death Penalty Information Center**, please also cite their reporting.

> Death Penalty Information Center.\
> <https://deathpenaltyinfo.org/executions/execution-database>

Additionally, the **ACLU of Delaware** and **ACLU of Tennessee** assisted with the collection of death records for Delaware state prisons.\
<https://www.aclu-de.org/>
<https://www.aclu-tn.org/>

## Data Notes

-   **New Jersey (NJ):** People who died in the Special Treatment Unit (STU) were excluded.\
    These individuals are considered civilly committed rather than incarcerated under DOC custody.

-   **Wisconsin (WI):** One individual listed as having died in "Other State" in 2024 was excluded,\
    as no context was provided to identify which state this referred to.

## License

Our data is licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-nc-sa/4.0/). That means that you must give appropriate credit, provide a link to the license, and indicate if changes were made. You may not use our work for commercial purposes, which means anything primarily intended for or directed toward commercial advantage or monetary compensation.

## Contact Us

For questions or feedback about the data, please reach out to [bbdp.data\@law.ucla.edu](mailto:bbdp.data@law.ucla.edu){.email}.
