# Titanic and Retail Sales Exploratory Data Analysis

This repository contains a Jupyter notebook exploring two prepared tabular datasets: Titanic passenger survival data and retail item outlet sales data. The notebook uses summary statistics and visualizations to inspect distributions, missing values, relationships, and potential outliers.

## Repository Contents

| File | Description |
| --- | --- |
| `Eda_cleaned.ipynb` | Python notebook containing the exploratory analysis and visualizations. |
| `data_cleaned.csv` | Prepared Titanic dataset with 891 records and 25 columns. The `Survived` column is the outcome; categorical fields are represented as indicator columns. |
| `train_cleaned.csv` | Prepared retail sales dataset with 8,523 records and 46 columns. `Item_Outlet_Sales` is the sales measure; categorical fields are represented as indicator columns. |

Despite its filename, `train_cleaned.csv` is not the Titanic training table: its columns describe retail items and outlets. Check the CSV headers before using either file in another workflow.

## Analysis Included

The notebook:

- Loads the prepared CSV files into pandas DataFrames.
- Inspects sample rows, data types, descriptive statistics, columns, and null counts.
- Uses box plots to inspect Titanic passenger age and fare distributions.
- Plots Titanic survival counts and the relationship between age, fare, and survival.
- Plots the retail sales distribution, item maximum retail price versus outlet sales, and item-weight distribution.

The notebook imports several scikit-learn estimators and metrics, but the cells currently present focus on exploratory data analysis; they do not train or evaluate a predictive model.

## Dataset Fields

### Titanic (`data_cleaned.csv`)

- `Survived`: survival outcome (0 or 1).
- `Age`, `Fare`: numeric passenger attributes.
- `Pclass_1` through `Pclass_3`: passenger-class indicator columns.
- `Sex_female`, `Sex_male`: sex indicator columns.
- `SibSp_*`, `Parch_*`: encoded sibling/spouse and parent/child counts.
- `Embarked_C`, `Embarked_Q`, `Embarked_S`: embarkation-port indicator columns.

### Retail Sales (`train_cleaned.csv`)

- `Item_Weight`, `Item_Visibility`, `Item_MRP`: item attributes.
- `Outlet_Establishment_Year`: outlet establishment year.
- `Item_Outlet_Sales`: item sales at an outlet.
- `Item_Fat_Content_*`, `Item_Type_*`: encoded item categories.
- `Outlet_Identifier_*`, `Outlet_Size_*`, `Outlet_Location_Type_*`, `Outlet_Type_*`: encoded outlet attributes.

The retail fat-content indicators retain multiple label variants (for example, `Low Fat` and `low fat`). Review and normalize category labels before modeling or comparing those categories.

## Getting Started

### Requirements

- Python
- Jupyter Notebook or JupyterLab
- The libraries imported by the notebook: `pandas`, `numpy`, `seaborn`, `matplotlib`, `plotly`, `altair`, and `scikit-learn`

Install the dependencies in your chosen Python environment:

```bash
python -m pip install pandas numpy seaborn matplotlib plotly altair scikit-learn jupyter
```

### Run the Notebook

1. Clone or download this repository and open its folder.
2. Install the requirements above.
3. In `Eda_cleaned.ipynb`, update the two CSV paths to use files in the repository. For example, replace the existing machine-specific paths with:

   ```python
   from pathlib import Path
   import pandas as pd

   project_dir = Path.cwd()
   df = pd.read_csv(project_dir / "data_cleaned.csv")
   df1 = pd.read_csv(project_dir / "train_cleaned.csv")
   ```

4. Start Jupyter from the repository directory, open `Eda_cleaned.ipynb`, and run the cells from top to bottom.

The notebook currently uses absolute paths from its original Windows environment (`D:\Machine_learning\DataSet\...`). Those paths will not work on other machines; use the project-relative example above or set paths appropriate for your local setup.

## Notes and Limitations

- The CSV files are prepared/encoded datasets. This repository does not include the original raw datasets or a documented cleaning pipeline, so the exact cleaning and encoding decisions cannot be reconstructed from these files alone.
- No dependency lockfile or `requirements.txt` is included; the install command above lists the libraries imported in the notebook.
- Dataset provenance and licensing details are not recorded in the files currently included. Add the source and applicable license information before redistributing the data publicly.
- The prepared tables have the same record count, but represent separate datasets and should not be combined.
 The prepared tables represent separate datasets and should not be combined.

## License

No license is specified in this repository. Add a license file if you intend to grant others permission to use, modify, or redistribute the code or data.