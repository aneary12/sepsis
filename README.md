# Sepsis Project

## Files

- **patient_selection.ipynb:**
    - this notebook queries the MIMIC-III database for patient details.
    - any patients not on their first ICU admission, or under 18 years old are excluded.
    - a quick visualisation of the dataset is included.
    - the remaining patient details are saved in 'data' for later use.
- **feature_extraction.ipynb:** 
    - this notebook queries the MIMIC-III database for all the dynamic features (features that change over time).
    - returns a list of numpy arrays for each feature.
    - each element of a list is a numpy array of shape (n,2), where n = the number of measurements in that hospital admission.
    - the first column of each numpy array are datetimes, and the second column are measurement values.
    - a quick visualisation of one feature is included.
    - the outputs are saved to in 'data' for later use.
- **data (files in italics NOT uploaded to Github):**
    - db_details.npy contains the details necessary to connect to the MIMIC-III database.
    - SQL_queries.npy contains the SQL queries needed to extract the dynamic features in feature_extraction.ipynb.
    - *patients.npy contains patient details that were produced in patient_selection.ipynb.*
    - *raw_features.npy contains the data produced in feature_extraction.ipynb ('raw' because the data still needs processing later on).*
   
## Notes

- Don't forget that 'temp' in feature_extraction.ipynb currently still includes both Celsius and Fahrenheit measurements.