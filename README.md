# Predicting Used Car Prices

## Dataset
Analyzed a comprehensive dataset from [Kaggle](https://www.kaggle.com/datasets/austinreese/craigslist-carstrucks-data/data) encompassing 426,880 rows and 26 columns, focusing on various attributes like model, manufacturer, mileage, age, condition, etc.:
- `id`: Unique identifier for the listing.
- `url`: URL of the vehicle listing on Craigslist.
- `region`: Geographic region of the listing.
- `region_url`: Craigslist URL for the region.
- `price`: The listed price of the car
- `year`: Year of the vehicle manufacture.
- `manufacturer`: Vehicle manufacturer.
- `model`: Specific model of the vehicle.
- `condition`: Condition of the vehicle (e.g., new, used, etc.).
- `cylinders`: Number of cylinders in the vehicle's engine.
- `fuel`: Type of fuel the vehicle uses.
- `odometer`: Mileage on the vehicle.
- `title_status`: Legal status of the vehicle's title.
- `transmission`: Type of vehicle transmission.
- `VIN`: Vehicle Identification Number.
- `drive`: Type of drivetrain.
- `size`: Size category of the vehicle.
- `type`: Type of vehicle body.
- `paint_color`: Color of the vehicle.
- `image_url`: URL of the vehicle's image.
- `description`: Description provided in the listing.
- `county`: County where the vehicle is located (often missing).
- `state`: State where the vehicle is listed. lat: Latitude coordinate for the listing location.
- `long`: Longitude coordinate for the listing location.
- `posting_date`: Date and time when the listing was posted.

## Data Preprocessing and Cleaning Overview
**1. Column Removal:**
- Dropped unique identifiers like `id`, `url`, `image_url`, `VIN`.
- Removed `region` and `region_url` as other columns better indicate the car`s location.
- Excluded columns with high missing data, such as `county` (100% missing) and `size` (72% missing).

**2. Handling Duplicates:**
Identified and removed duplicate entries to ensure data uniqueness.

**3. Missing Values Management:**
- Eliminated rows with missing values in columns where missing data was minimal (about 10%).
- For categorical columns with missing data, replaced missing values with `unknown`.

**4. Data Subsetting:**
- Focused on data from the year 2013 onwards.
- Applied the Interquartile Range (IQR) method for `odometer` and `price`.

**5. Data Type Conversion:**
- Converted `year` and `odometer` to integers.
- Transformed `posting_date` to datetime format.

**6. Feature Engineering:**
Created a new feature `car_age` calculated as the maximum year in the dataset minus the car`s year plus one (to account for models sold a year before their model year).

## Model Analysis and Evaluation
**1. Feature Selection:**
Utilized 14 independent variables, including manufacturer, model, condition, cylinders, fuel type, odometer reading, title status, transmission type, drive type, vehicle type, paint color, latitude, longitude, and car age.

**2. Target Variable:**
The dependent variable was the `price` of the used cars.

**3. Data Split:**
Divided into training, validation, and test sets with a 60-20-20 split, encompassing 185,853 records in total.

**4. Feature Processing:**
Numerical features standardized using StandardScaler and categorical features encoded using OneHotEncoder, resulting in 8,217 processed variables.

**5. Model Performance:**
- Lasso Regression (alpha=0.01) achieved an **R² of 0.8756** on the validation set.
- Random Forest (n_estimators=200) showed an **R² of 0.9101** on the validation set.
- Random Forest model was the top performer, with an **R² of 0.9134** on the test set, indicating superior predictive accuracy.

## Practical Application
Demonstrated the model's real-world applicability by predicting the price of a team member's car. The prediction aligned closely with Kelley Blue Book's private party range, validating the model's accuracy.

## Team Collaboration
Worked within a team of 5, contributing to data preprocessing, model development, and result analysis. Overcame challenges related to data cleaning, high dimensionality, and model complexity.

## Libraries used
NumPy, pandas, Seaborn, sklearn, time
