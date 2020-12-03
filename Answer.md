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

It shows the heatmap of the samples with different metadata like histological type, ethinicity, vital status etc and below, the heatmap is between genes and samples.

Ans 1: 
a) Behaviour of sample can be seen on various aspects present in column metadata file. One of the aspect was histological type where the tumours were divided into adenocarcinoma and neuroendocrine. By plotting this, we saw adenocarcinoma sample are forming dense cluster while Neuroendocrine showing low denser.

b) Some of the neuroendocrine tumours are clrearly separable from adenocarcinoma tumours but very few are overlapped with adenocarcinoma tumours. They were seperated successfully.

c) Varaince ratio of the PCA two components is percentage of variance explained by each of the selected components.It came out to be 0.16429956 and 0.11939836. This signifies first component has more variance than second component. 

# Interferons

Interferons (IFNs) are a group of signaling proteins made and released by host cells in response to the presence of several pathogens, such as viruses, bacteria, parasites, and also tumor cells. Type I interferons (IFNs) are a large subgroup of interferon proteins that help regulate the activity of the immune system. The genes responsible for type 1 Interferons is called Type 1 IFN signature and consists a set of 25 genes in homo sapiens.

![alttext](https://user-images.githubusercontent.com/75350171/100987070-07e72780-3574-11eb-8996-45739dbf2127.PNG)

This heatmap shows the plot between 19 genes and 167 samples out of 25 human interferons (because .loc function of python was giving error in selecting all 25). The samples contains all endocrine tumour samples. Most values are between 15 and 10 which shows gene distribution across all samples to be of high expression. Few genes have low expression. 

GSVA was a new topic for me and I explored the information given regarding the package. So I tried using GSVA in python but there seems to be problem in .loc[ ] function, so I gave a supposed code of gsva in python as to how its used. The GSVA is done by doing tsne plot of expression file with genes in intereferon files. I couldn't use the Docker for GSVA because I didn't have ubuntu os.

Ans 2:
a) Yes, I can characterise the presence of IFN genes into adenocarcinoma tumours by assigned score to each gene per histological type.

b) Distribution will depened upon the plot which comes by performing tsne.The position of dots will tell the distribution pattern. If the clusters are visible then they aren't well dispered. 

c) Yes, we can identify the presence of IFN in PAAD subtypes. We saw this even in heatmap above that high expression means presence of IFNs in PAAD.
