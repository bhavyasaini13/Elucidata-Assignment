# Elucidata-Assignment

Assignment based on Gene expression analysis for Pancreatic Cancer.

Introduction: Pancreatic Adenocarcinoma (PAAD) is the third most common cause of death from cancer, with an overall 5-year survival rate of less than 5%, and is predicted to become the second leading cause of cancer mortality in the United States by 2030. RNA sequencing is used to check the amount of RNA in a given biological sample. I had a dataset conatining 18,465 genes and 183 tumor samples, in GCT format which had 3 dataframes combined together. 

1. Main dataframe which has 18465 genes and 183 samples.
2. Row metadata which has 18465 gene names only.
3. Column metadata which has 183 sample names and 124 rows of metadata like patient id, vital status, histological type, ethinicity etc.

I.  Data Preparation
For preparing data, first imported data as matrix and dataframe from GCT file. Then, NaN values were omitted and finally 14098 genes were remained with 183 samples.Heatmap of gene expression data was created to see gene distribution. 

![alttext](https://user-images.githubusercontent.com/75350171/100968435-5934ee00-3557-11eb-9dac-f74e95e7231b.PNG)

The heatmap shows expression of genes in the sample. Yellow signifies high expression and blue signifies low expression. Thus we see mainly pink/red colour in heatmap which suggests that the genes shows high expression. Blue tiles shows the low expression of that gene in the sample. X axis has gene ids and Y axis has sample info. 

II. PCA Algorithm 
PCA stands for Principle Componenet Analysis. It a dimensionality reduction technique which is based on variance and eigen values. Here, we have reducted the dimentionality of the data and variance is calculated for PCA. As I have selected 2 components, I got variance and variance ratio for those 2 components. 
Now, we have to seperate endocrine tumours from exocrine tumours on the basis of 'histological_type_other'. The PCA plot is created: 

![alt text](https://user-images.githubusercontent.com/75350171/100971603-47564980-355d-11eb-9009-c4eba8ff8175.PNG)

In the plot, Purple, darkblue, orange, maroon are for neuroendocrine and rest colours are for adenocarcinoma. By the look of it, above stated colours are less in frequencey and pink are most, thus seperating the two types of tumours. The data is clearly seperated into lower and upper side with majority of samples in lower side. Next step was eliminating these outliers as majority samples are situated between -100 to 100 for Value1 (on X axis) and less than 50 for Value2 (on Y axis).
Thus, our data now contained adenocarcinoma samples without the outliers.

# Visualization by Phantasus tool.
![alttext](https://user-images.githubusercontent.com/75350171/100973506-aec1c880-3560-11eb-9d54-00d6b5313132.png)
![alttext](https://user-images.githubusercontent.com/75350171/100973515-b1242280-3560-11eb-9999-1b09e086d36c.png)
