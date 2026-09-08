# JS02: Data Preprocessing Lab Report

## JS02.01: Getting to Know the Data

Lab 1 was all about getting familiar with the Titanic dataset before touching anything. The dataset has 891 rows and 12 columns, things like PassengerId, Survived, Pclass, Name, Sex, Age, SibSp, Parch, Ticket, Fare, Cabin, and Embarked. I used `head()`, `shape`, `info()`, `isnull().sum()`, and `describe()` to get a feel for the structure, data types, and how much data was actually missing.

For the numeric columns, mainly Age and Fare, I plotted histograms to see how the values were distributed, and boxplots to check Fare for outliers. I also used a correlation heatmap and a scatter plot of Age vs. Fare to see if there was any relationship worth noting between the two.

The main takeaway: Age, Cabin, and Embarked all have missing values, so the dataset clearly needs some cleanup before it's usable for anything further.

**Conclusion:** Before jumping into preprocessing, it's worth spending time understanding the data's shape, types, gaps, and relationships, it saves headaches later.

---

## JS02.02: Cleaning Up the Data

In Lab 2, I tackled the missing values found earlier. Age was filled in with its average value, Cabin (which had a ton of missing entries) was filled with a placeholder `"DECK"`, and Embarked was filled using its most common value (the mode). Once that was done, I saved the cleaned dataset as `Titanic-Dataset-Fixed.csv`.

Checking the dataset afterward confirmed that Age and Cabin no longer had any missing values, and the dataset still had all 891 rows and 12 columns, nothing lost in the process.

**Conclusion:** Handling missing values properly gets the dataset into a much more usable state for the next steps.

---

## JS02.03: Encoding and Scaling

Lab 3 picked up where Lab 2 left off, using the cleaned dataset. I narrowed things down to five columns: Survived, Pclass, Age, Sex, and Cabin. Since Sex and Cabin are categorical (text-based), I converted them into numbers using LabelEncoder.

I then standardized Age using StandardScaler, which rescales the values so they're centered around a mean of 0, some values end up negative, some positive, depending on how far they are from the average.

By the end, the categorical columns were fully numeric, and Age was on a standardized scale ready for modeling.

**Conclusion:** Encoding and scaling are what actually make the data digestible for machine learning algorithms.

---

## JS02.04: Working with Images

Lab 4 shifted gears to image data using the classic Lenna image. First, I loaded and displayed it in its original form. Then I resized it down to 128×128 pixels.

After resizing, I converted the image to grayscale, stripping out the color information and leaving just brightness levels, a much simpler representation than the original RGB image.

**Conclusion:** Preprocessing isn't just for tables, it applies to images too. Resizing keeps dimensions consistent, and grayscale conversion strips things down to the essentials.

---

## JS02 Assignment: Wisconsin Breast Cancer Dataset

For the assignment, I worked with the Wisconsin Breast Cancer dataset, 569 rows and 33 columns, including `id`, `diagnosis`, a bunch of cell measurement features, and an oddly-named `Unnamed: 32` column. I dropped `id` and `Unnamed: 32` right away since neither is useful for analysis.

The `diagnosis` column (malignant/benign) was label-encoded into a new `diagnosis_encoded` column, for example, `M` (malignant) became `1`. After that, I standardized all the numeric feature columns using StandardScaler, but deliberately left `diagnosis_encoded` untouched since it's the target label, not a feature to be scaled.

The end result: diagnosis is now numeric, and features like `radius_mean` and `area_mean` are all on a standardized scale.

**Conclusion:** This assignment covered the essentials of preprocessing, dropping unnecessary columns, encoding the target label, and standardizing the features, leaving the dataset in solid shape for modeling and feature selection down the line.
