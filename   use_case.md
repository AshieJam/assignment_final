# Use Case: Remote Patient Monitoring (RPM) Mini-Pipeline for Diabetes Wearables

## Problem Statement
Diabetes management increasingly relies on continuous glucose monitoring (CGM) wearables such as Dexcom and Abbott FreeStyle Libre. These devices generate frequent glucose readings that provide valuable insights into glycemic control, hypoglycemia risk, and glucose variability. However, many clinics struggle to integrate wearable data into a consistent, scalable workflow that allows care teams to monitor patients between visits.

Wearable data is often siloed in vendor portals, uploaded inconsistently, or reviewed only during scheduled appointments. This limits timely intervention and reduces the potential benefits of remote patient monitoring (RPM) programs.

This project proposes a cloud-based RPM mini-pipeline that ingests CGM data from multiple wearable vendors, standardizes the data into a unified format, computes clinically meaningful summary metrics, and presents these summaries to clinicians through a lightweight dashboard.

## Users
- **Patients:** Wear CGM devices and authorize data sharing or upload device exports  
- **Care managers / nurses:** Monitor trends and identify patients requiring follow-up  
- **Clinicians (PCPs / endocrinologists):** Review summarized glucose patterns to guide treatment decisions  
- **Clinic IT / operations staff:** Maintain system access, data quality, and monitoring  

## Data Sources
This project uses de-identified or tokenized data appropriate for a student environment.

### 1. CGM Readings (Primary)
- Format: CSV or JSON  
- Example fields:
  - `patient_token`
  - `device_vendor` (Dexcom / FreeStyle Libre)
  - `timestamp`
  - `glucose_mg_dl`
  - `trend_indicator`
- Source: Device exports or simulated vendor API feeds  

### 2. Device Events (Optional)
- Format: JSON  
- Example fields:
  - `timestamp`
  - `event_type` (meal, insulin, exercise)
  - `notes`

### 3. Patient Metadata
- Format: Database table  
- Example fields:
  - `patient_token`
  - `rpm_program_status`
  - `monitoring_start_date`

### 4. System-Generated Summaries
- Format: Database tables  
- Metrics:
  - Average glucose
  - Time-in-range
  - Time below range
  - Time above range
  - Weekly alert flags

## Basic Workflow
1. CGM devices generate glucose readings continuously  
2. Data is uploaded or transferred securely to the cloud  
3. Raw CGM files are stored in cloud object storage  
4. Serverless functions validate and standardize incoming data  
5. Cleaned data is loaded into a managed SQL database  
6. Scheduled analytics compute weekly summaries and flags  
7. Clinicians access summarized results via a dashboard  
