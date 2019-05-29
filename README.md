# Genetic-Variant-Classifications

## Context
ClinVar is a public resource containing annotations about human genetic variants. These variants are (usually manually) classified by clinical laboratories on a categorical spectrum ranging from benign, likely benign, uncertain significance, likely pathogenic, and pathogenic. Variants that have conflicting classifications (from laboratory to laboratory) can cause confusion when clinicians or researchers try to interpret whether the variant has an impact on the disease of a given patient.

## Content
The objective is to predict whether a ClinVar variant will have conflicting classifications. This is presented here as a binary classification problem, where each record in the dataset is a genetic variant.

![Test Image 1](https://raw.githubusercontent.com/arvkevi/clinvar-kaggle/master/clinvar-class-fig.png)

Conflicting classifications are when two of any of the following three categories are present for one variant, two submissions of one category are not considered conflicting.

Likely Benign or Benign
VUS
Likely Pathogenic or Pathogenic
Conflicting classification has been assigned to the CLASS column. It is a binary representation of whether or not a variant has conflicting classifications, where 0 represents consistent classifications and 1 represents conflicting classifications.

Since this problem only relates to variants with multiple classifications, I removed all variants from the original ClinVar .vcf which only had one submission.

The raw variant call format (vcf) file was downloaded here on Saturday, April 7th, 2018: ftp://ftp.ncbi.nlm.nih.gov/pub/clinvar/vcf_GRCh37/clinvar.vcf.gz

## Summary of Modeling
Predicted conflicting classifications for  ClinVar variants:

• Explore features in Genetic Variant with Python Matplotlib, Seaborn

•  Standardized numerical features by StandardScalar too improve the performance of machine learning algorithms such as Logistic Regression and SVM

• Mitigate overfitting and tuned hyper-parameters for Stochastic Gradient Descent and Random Forest models via GridSearchCV

• Created a pipeline of optimized Logistic Regression, Stochastic Gradient Descent and AdaBoostClassifier with SMOTE in order to achieve better predictors

• Stacked top three optimized models by assigning the highest weight to the best model to create the ultimate predictor and decrease the False Negative rates. The final result of the stacked model improved by 36%
