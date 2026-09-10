Rapido --- Captain Acquisition & Supply Assessment
Overview
This repository contains the working analysis for the Rapido Captain Acquisition & Supply take-home assessment.

The analysis is organized into:

Part A --- Captain acquisition
A1: Signup → Approval funnel
A2: Largest fixable onboarding leak and segment analysis
A3: CAMP_WA_002 campaign evaluation
A4: Recommendations synthesized from A1--A3
Part B --- Airport supply
B1: Airport demand--supply mismatch
B2: Post-airport return-fare experience
B3: Whether targeted acquisition is the right intervention
The assessment is designed to be reproducible from the supplied raw CSV files.

Folder Structure
Rapido_Assessment/
│
├── Memo.pdf
├── Deck.pptx
├── README.md
│
├── Working/
│   ├── A1Task.ipynb
│   ├── A2Task.ipynb
│   ├── A3Task.ipynb
│   ├── B1Task.ipynb
│   ├── B2Task.ipynb
│   └── B3Task.ipynb
│
└── Data/
    ├── captains.csv
    ├── doc_events.csv
    ├── approvals.csv
    ├── activation.csv
    ├── nudges.csv
    ├── airport_hourly.csv
    └── airport_trips.csv
If the notebooks and CSVs are kept in a different folder structure, update the path variable in each notebook accordingly.

Requirements
Python 3.x with:

pandas
numpy
jupyter
Install the dependencies with:

pip install pandas numpy jupyter
No external database or API is required.

How to Run
Run the notebooks in the following order:

A1Task.ipynb
      ↓
A2Task.ipynb
      ↓
A3Task.ipynb
      ↓
B1Task.ipynb
      ↓
B2Task.ipynb
      ↓
B3Task.ipynb
Each notebook loads the required raw CSV files directly.

A1 --- Funnel
Uses:

captains.csv
approvals.csv
doc_events.csv
The May 2026 signup cohort is used for the acquisition funnel because the data is extracted at the end of June 2026 and June contains a meaningful in-progress population.

A2 --- Acquisition Leak
Uses:

captains.csv
doc_events.csv
approvals.csv
The analysis examines document verification failures, failure reasons and segment-level differences to identify an actionable onboarding leak.

A3 --- CAMP_WA_002
Uses:

captains.csv
approvals.csv
nudges.csv
The campaign comparison reports an observed association between campaign targeting and approval. It is treated as observational rather than causal because campaign assignment was not randomized.

B1 --- Airport Supply
Uses:

airport_hourly.csv
The analysis identifies hourly airport-terminal demand and supply mismatch, with particular focus on the late-night period.

B2 --- Post-Airport Experience
Uses:

airport_trips.csv
The analysis measures whether airport trips receive a return fare within 20 minutes and compares the outcome by destination type and trip distance.

B3 --- Intervention Decision
Combines the B1 and B2 findings to assess whether additional targeted captain acquisition is the best intervention for the airport supply problem.

Key Definitions
A2O
Approval-to-Order / Signup-to-Approval funnel metric used in the assessment:

A2O = approved captains / signups
R2A
Signup → first order.

Required document sequence
The onboarding document sequence is:

DL → RC → Aadhaar → Permit (Auto/Cab) → Fitness → Insurance
ERickshaw does not require the Permit stage.

Important Data / Analysis Notes
Cohort censoring
The dataset is extracted at:

2026-06-30 23:59 IST
Therefore, June signups can have incomplete onboarding journeys. The May cohort is used for the main acquisition conversion analysis to reduce this censoring issue.

Campaign interpretation
The CAMP_WA_002 result is an observed difference, not a causal treatment effect.

The analysis therefore recommends a randomized holdout before materially increasing campaign scale.

Airport-trip limitation
airport_trips.csv does not contain a captain ID.

Therefore, B2 can measure trip-level return-fare outcomes but cannot directly establish individual captain behavior or prove that poor return-fare availability caused captains to leave airport supply.

Failure-event counts
Document failure events can include multiple events for the same captain and multiple failure types. They should therefore not automatically be interpreted as unique captains or as one-for-one recoverable approvals.

Main Outputs
The final deliverables are:

Memo
A maximum two-page decision memo for the Head of Supply, focused on findings, implications and recommendations rather than code or detailed methodology.

Deck
A maximum six-slide presentation summarizing the most important findings and recommendations.

Working
The notebooks provide the reproducible analysis from the raw CSVs.

Reproducibility
To reproduce the analysis:

Place all seven raw CSV files in the Data/ directory.
Open the notebooks from the Working/ directory.
Update the data path if necessary.
Run the notebooks in order.
Review the printed tables and analysis outputs.
The memo and deck summarize the resulting findings.
All analysis is performed using the supplied assessment data; no external data source is required.
