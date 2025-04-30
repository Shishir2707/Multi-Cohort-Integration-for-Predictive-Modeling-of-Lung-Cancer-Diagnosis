# Multi-Cohort-Integration-for-Predictive-Modeling-of-Lung-Cancer-Diagnosis


This project demonstrates a robust pipeline for identifying a minimal gene signature for lung cancer diagnosis by integrating multiple GEO datasets, performing differential expression analysis, visualization, and training a Random Forest classifier with internal and external validation.

The code for this project was written in python in google collab.


Datasets Used :
GSE18842, GSE19804, GSE19188 - Core training datasets ( First 2 were used in Paper I selected for presentation )
GSE31210, GSE33532 - Used as Additonal and  Externally Validating the model.


Packages Required :
GEOparse – for downloading and parsing GEO datasets
gseapy – for gene set enrichment analysis
umap-learn – for Uniform Manifold Approximation and Projection
scikit-learn – for machine learning 
matplotlib – for plotting
seaborn – for advanced visualizations
pandas – for data handling and manipulation
numpy – for numerical operations
scipy – for statistical tests

Input Files :
No Input files are required to upload manually as required files/datasets as i have writnen scrript to fetch required files directly from web.

Steps done:

I downloaded expression data using GEOparse first , then each dataset is parsed, cleaned, and normalized, with tumor and normal samples labeled based on metadata.
As above mentioned Dataset was was fetched from Web directly. Further I used two dimensionality reduction techniques — PCA and UMAP. Both of these allowed me to visualize the pattern of the data and told me that tumor and normal samples were splitting into distinct clusters, which was a good sign that the gene expression profiles had meaningful biological information. I then pulled out the genes which were differently expressed among different datasets and narrowed down the list to a list of 37 repeat genes. I cross-mapped them over to gene symbols and analyzed by enrichment so that I could find out through which biological processes or pathways these were functioning. It put the data in a place of biological significance and also inferred the findings.

Following this, I them trained a Random Forest classifier on these 37 genes and wished to verify whether they would differentiate the normal and tumor samples correctly. In internal testing, the model performed wonderfully. I went ahead and analyzed the top genes responsible for the prediction of the model and, using this information, built a lean, minimalist model consisting of only the top five genes: GOLM1, GRK5, SPP1, CDH5, and ROBO4. To verify that the model was not overfitting, I cross-validated it using a totally different dataset (GSE31210), and it worked extremely well once again — with a approximate 94% accuracy and an AUC of 0.98. Finally, I summarized the findings using visualizations like heatmaps, confusion matrices, and ROC curves to show how good the model worked and how this process can be used to aid future diagnostic procedures in lung cancer


Output Files :

Mapped_37_DEGs.csv	- 37 common DEGs with gene symbols
GO_Enrichment_Results.csv, KEGG_Enrichment_Results.csv -	Pathway analysis outputs
Top_10_Important_Genes.csv -	Feature-ranked genes

Along with files , there are more output images of results. They are uploaded in results folder with following names
Confusion Matrix
External Validation Confusion Matrix
External Validation ROC
GSE33532
GSE312210
Heatmap top 10 Genes
Heatmap  ( top 5 Genes )
PCA GSE18842
PCA GSE19804
ROC Curve
Top 10 Important Genes
Top 15 Important Genes
Venn Daigram (Command DEGs)
Volcano Plot 1 DR UR
VP 2
VP 3

Steps to Run Script
#Run cooomand given below 
!pip install GEOparse gseapy umap-learn scikit-learn matplotlib seaborn pandas numpy scipy

#Then upload and run the notebook attached here.


Note - To test clear functionality of code , I suggest running code in blocks/chunks  , however whole script can be run at once.
#There are few optional steps ( classification of top 5 genes etc ) is also carried out in end of code , but its not required for main project work and is totally optional.
