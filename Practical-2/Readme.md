# Label Encoding and PCA Implementation

This repository demonstrates the implementation of **Label Encoding** and **Principal Component Analysis (PCA)** using Python. The code includes preprocessing, encoding categorical variables, dimensionality reduction, and visualization of PCA results.

## Dataset
Two datasets are used in this implementation:
1. `cars.csv`: Contains details about cars, including features like `brand`, `fuel`, and `owner`.
2. `Customer.csv`: Contains customer data, including attributes like `gender`, `review`, `education`, and `purchased`.

## Prerequisites
- Python 3.6+
- Required libraries: 
  - `pandas`
  - `scikit-learn`
  - `matplotlib`

## Implementation Details

### 1. **Label Encoding**
Label Encoding is used to convert categorical variables into numerical representations. This step is crucial for machine learning algorithms that require numerical input.

#### Steps:
1. Import the dataset:
   ```python
   import pandas as pd
   df = pd.read_csv('cars.csv')
   df1 = pd.read_csv('Customer.csv')
   ```
2. Handle missing values:
   ```python
   pd.isnull(df).sum()
   ```
3. Apply Label Encoding:
   ```python
   from sklearn.preprocessing import LabelEncoder
   label_encoder = LabelEncoder()

   # Encoding for cars dataset
   df['brand_encoded'] = label_encoder.fit_transform(df['brand'])
   df['fuel_encoded'] = label_encoder.fit_transform(df['fuel'])
   df['owner_encoded'] = label_encoder.fit_transform(df['owner'])

   # Encoding for customer dataset
   df1['gender_encoded'] = label_encoder.fit_transform(df1['gender'])
   df1['review_encoded'] = label_encoder.fit_transform(df1['review'])
   df1['education_encoded'] = label_encoder.fit_transform(df1['education'])
   df1['purchased_encoded'] = label_encoder.fit_transform(df1['purchased'])
   ```
4. Drop original categorical columns:
   ```python
   df.drop(['brand', 'fuel', 'owner'], axis=1, inplace=True)
   df1.drop(['gender', 'review', 'education', 'purchased'], axis=1, inplace=True)
   ```

### 2. **Principal Component Analysis (PCA)**
PCA is used to reduce the dimensionality of the dataset while preserving most of the variance.

#### Steps:
1. Standardize the data:
   ```python
   from sklearn.preprocessing import StandardScaler
   scaler = StandardScaler()
   scaled_data = scaler.fit_transform(df)
   ```
2. Apply PCA:
   ```python
   from sklearn.decomposition import PCA
   pca = PCA(n_components=2)
   pca_result = pca.fit_transform(scaled_data)
   ```
3. Create a DataFrame for PCA results:
   ```python
   import pandas as pd
   pca_df = pd.DataFrame(data=pca_result, columns=['PC1', 'PC2'])
   ```
4. Visualize PCA results:
   ```python
   import matplotlib.pyplot as plt
   plt.figure(figsize=(8, 6))
   plt.scatter(pca_df['PC1'], pca_df['PC2'], color='blue', alpha=0.7)
   plt.title('PCA Visualization')
   plt.xlabel('Principal Component 1')
   plt.ylabel('Principal Component 2')
   plt.grid()
   plt.show()
   ```

## Key Outputs
1. Label Encoded Data:
   - Transformed categorical variables into numerical form.
   - Example for the `cars` dataset:
     ```
     brand  fuel  owner  brand_encoded  fuel_encoded  owner_encoded
     Toyota Petrol First  2              3             1
     ```
2. PCA Visualization:
   - Scatter plot showing the reduced 2D data from the original dataset.

## Dependencies
Install the required libraries using pip:
```bash
pip install pandas scikit-learn matplotlib
```

## How to Run
1. Clone the repository.
2. Place the `cars.csv` and `Customer.csv` datasets in the same directory.
3. Execute the script to see the results:
   ```bash
   python script_name.py
   ```

## References
- [Pandas Documentation](https://pandas.pydata.org/docs/)
- [Scikit-learn Documentation](https://scikit-learn.org/stable/)
- [Matplotlib Documentation](https://matplotlib.org/stable/)

