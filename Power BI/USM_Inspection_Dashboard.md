## Introduction
Ultrasonic Meter Report Inspection dashboard aims to simplify Subject Matter Expertises(SMEs)' process to identify problems in the report, including failing inspections,  missing work order (WO)s, and data accuracy. There are three primary requirements for the dashboard:  
1) Identify the reasons for each Further Investigation Required
2) Ensure all the documents having 'further investigation recommended' answered to 'Yes' have corrective work order created and properly addressed
3) Identify the gaps between report data and SAP Master data

## Relationship Models
The following images are the high level view of the relationship model and the screenshot of the model created for the dashboard. There are two types of Ultrasonic Meters: 1) Krohne, 2) Daniel, so the model here contains both types and users can see the data visualization for both types of meters. 
The tables are encircled within a red box and a orange box.<br />
$${\color{red}RED}$$: These tables are used for identifying the work orders and inspection reports for each quarter and each station.<br />
$${\color{orange}ORANGE}$$: These tables are used for identifying the reasons of further investigation recommended required. <br />

![Presentation1](https://github.com/user-attachments/assets/a84e90a7-3b40-4f7f-a035-6ececfc31330)
![image](https://github.com/user-attachments/assets/07669734-0c26-42c6-922a-91ff18a2dd24)

## Overview Page
This overview page shows the summary for Ultrasonic Meter reports. 
![image](https://github.com/user-attachments/assets/5b145ab1-47fe-450f-b0c4-b3767e156b25)

## First Requirement Visualization
**The first requirement of the dashboard is to ensure that user can find a particular report when they select any of the report’s failed (alarm/warning) fields as the filter.** <br />

Since report that requires further investigation has multiple warning/alarm fields, a summary column (**FailTypeSum**) is needed in both USM Inbox-Daniel RI and USM Inbox-Krohne RI to track all the warning/alarm fields of the reports. The summary column is the primary key for each table and shows the failtype(s) each report has. <br />
**FailTypeSum** is the foreign key of **Krohne Fail Key/ Daniel Fail Key**, which contains the breakdown to individual fail types of each fail type summary. This breakdown column is used in the folllwing page so the user will be able to find a report by filtering on any of its fail types.<br />
![image](https://github.com/user-attachments/assets/3b1567ac-97c8-4442-b70a-270a066084bf)


## Second Requirement Visualization
**The second requirement of this dashboard is to be able to see for each station each quarter:** <br />
1) Is there a PM03 order? 
2) Is there a USM inspection Report 
3) Is there a PM01/PM02 Work Order if further investigation recommended is answered to ‘Yes’
This requirement is achieved by building a matrix that has quarter as the y-axis and station as the x-axis. Values are taken from **USM Daniel/Krohne**, **M1/M2 WO** and **M3 WO**. These value columns solve the above questions respectively. The skeleton of this matrix is a corssjoin between all the Krohne/Daniel Stations and the calendar table.
![image](https://github.com/user-attachments/assets/9a624884-51f0-4a3a-ad0c-a7e4ac6945a7)
## Third Requirement Visualization
### SAP Gap Analysis
SAP gap analysis is also included in the report to identify gaps between serial numbers, manufacturer models, and station names recorded in Ultrasonic Meter report and SAP Master data. This page aims to help users identify the discrepencies and faciliate trainings to stakeholders and bridge the gap between manual entry and system record.
![image](https://github.com/user-attachments/assets/a2cfc717-1ebe-43b5-b408-80fd189875c2)


### Work Order Analysis
This page is used to match each report with its WO and identify which WO has a missing report in the system.

![image](https://github.com/user-attachments/assets/098b03a1-7eaa-4a95-b45d-ea5ef94ab705)
