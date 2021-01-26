# Sepsis Project

## Files

- **patient_selection.ipynb:**
    - this notebook queries the MIMIC-III database for patient details.
    - any patients not on their first ICU admission, or under 18 years old are excluded.
    - any patients who spend less than 24 hours in ICU are excluded.
    - a visualisation of the dataset is included.
    - the remaining patient details are saved in the 'data' folder for later use.
- **feature_extraction.ipynb:** 
    - this notebook queries the MIMIC-III database for all the dynamic features (features that change over time).
    - returns a list of numpy arrays for each feature.
    - each element of a list is a numpy array of shape (n,2), where n = the number of measurements in that hospital admission.
    - the first column of each numpy array are datetimes, and the second column are measurement values.
    - a visualisation of one feature is included.
    - the outputs are saved in the 'data' folder for later use.
 - **static_features.ipynb:** 
    - this notebook queries the MIMIC-III database for all the static features (features that don't change over time).
    - returns a numpy array for each feature.
    - each row of an array represents a patient, and each column is a binary variable for a different feature.
    - a visualisation of the two features is included.
    - the outputs are saved in the 'data' folder for later use.
- **time_series_generation.ipynb:** 
    - this notebook does some pre-processing on the data in raw_features.npy (produced in feature_extraction.ipynb).
    - for every feature, the raw data is converted to an hourly time series for each patient.
    - a visualisation of the process is shown using one patient's heart rate data.
    - currently, 24-hour time series are being created (as all patients spend a minimum of 24 hours in the ICU), although this can be changed.
    - the value for a given hour is calculated by taking the mean of all measurements of values that fall within that hour. If no measurements were taken in that hour, then period in consideration is increased by an hour either side of the hour in question (i.e. 3 hours are considered, rather than just 1). The time window is gradually increased in this way until at least one measurement falls in that window, at which point the mean is taken.
    - the outputs are numpy arrays with shape (m,hrs), and they're saved in the 'data' folder for later use.
- **data (files in italics NOT uploaded to Github):**
    - db_details.npy contains the details necessary to connect to the MIMIC-III database.
    - SQL_queries.npy contains the SQL queries needed to extract the dynamic features in feature_extraction.ipynb.
    - static_queries.npy contains the SQL queries needed to extract the static features in static_features.ipynb.
    - *patients.npy contains patient details that were produced in patient_selection.ipynb.*
    - *raw_features.npy contains the data produced in feature_extraction.ipynb ('raw' because the data still needs processing later on).*
    - *static_features.npy contains the data produced in static_features.ipynb.*
    - *processed_features.npy contains the data produced in pre_processing.ipynb.*