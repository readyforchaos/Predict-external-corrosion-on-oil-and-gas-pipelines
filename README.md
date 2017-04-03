# DNV GL Machine Learning – Predict external corrosion on oil and gas pipelines

Microsoft sat down with DNV GL in their headquarters to execute on a five-day-hackathon where the focus was to predict external corrosion on pipelines using Machine Learning.

## Customer profile

DNV GL is an international certification body and classification society with main expertise in technical assessment, advisory, and risk management. It was created in 2013 because of a merger between two leading organizations in the field - Det Norske Veritas (Norway) and Germanischer Lloyd (Germany).

DNV GL is the world's largest classification society with 13,175 vessels and mobile offshore units (MOUs), which represents a global market share of 21%. The organization is also a reference in renewable, alternative and conventional energy. It is the world's largest technical consultancy to onshore and offshore wind, wave, tidal, and solar industries, as well as the global oil & gas industry – 65% of the world’s offshore pipelines are designed and installed to DNV GL’s technical standards. Microsoft worked with DNV GL in the Norwegian headquarters in Høvik from the Oil & Gas silo. 

[VERTICALS]

Read more about DNV GL at [Wikipedia](https://en.wikipedia.org/wiki/DNV_GL).

## Challenger story

Since the inception of the federal regulations in the US governing pipeline integrity and safety in the early 2000’s following several high-profile incidents, there has continued to be an unacceptable number of pipeline failures with major impacts on people, property, and the environment.

Since the inception of the regulations governing pipeline safety and integrity in the US is the early 2000’s there has continued to be a succession of high-profile failures. These failures are due not only to a combination of failure to adhere to recommended practices but also a failure of the methodologies and technologies currently recommended and implemented by most pipeline operators. In this period data-driven analytics and machine learning capabilities have come of age and are now practical technologies to be used in routine day to day operations (you and I use them every day, all day long!). Although, used to some level by high technology in pipe inspection companies the technology has not previously been used in practice by operations or considered appropriately by the standards and recommended practices bodies to advance the science of pipeline engineering.

DNV GL as renown experts in pipeline condition assessment realize the weaknesses of today and the strengths of the technology we now have on offer to us and have combined this to provide a software tool that harnesses deep learning analytics alongside engineering know-how and expertise in pipeline degradation expertise.

## Assessment

Assessment is made of a various combination of “appropriate” indirect inspections, the selection of which can be difficult and fragmented over long sections of the pipeline. From this, along with pipeline history, areas are prioritized for physical examination (direct assessment) and the state of the pipeline is determined based upon the corrosion observed in the pipeline at the locations of these excavations.

Inline Inspection Tool (ILI) pigging in the context of pipelines refers to the practice of using devices known as "pigs" to perform various maintenance operations. This is done without stopping the flow of the product in the pipeline. The reason the machines are called a “pig” is because it squeak’s when it goes through the pipes. It collects data through the use of magnetic flux leakage (MFL) and ultrasonic to inspect the pipeline. It uses electromagnetics to sense wall integrity which is transformed from waves to binary digits (digital signals).

### Image of an ILI Pig tool

[PIG]

### Heat map showing defects in pipe

[PIPE]

### Anatomy of the ILI Pig tool

[ILI]

## The objective

The objective is to produce a solution demonstrator that DNV GL can show to customers and also to their own internal groups to promote the technology and raise awareness of the role that analytics brings to their business and the solutions DNV GL delivers. The application is very much one which will have strong appeal in the market and the hackfest will simply be the beginning of something which will become a successful project/demonstrator that DNV GL can build upon and take to the next level.

DNV GL already has an internal tool that visualizes the pipelines around the world. The application is called “Synergi Pipeline” and is connected to a single database that consists of data from multiple data sources gathered/generated from partners and vendors. The web tool allows the users of Synergi Pipeline to do risk and analytical modeling, risk and activity management as well as doing inspection based on the overview. We decided to aim for implementation in Synergi Pipeline of the machine learning predictions based on the model leveraged through a web service in Microsoft Azure.

## The team

Company  | Name | Role
------------- | ------------- | -------------
DNV GL | Bran Eichelberger | Business sponsor
DNV GL | Tom Gilmour | Business sponsor
DNV GL | Jeff Lanchey | BA collaborator
DNV GL | Troy Weyant | Consulting collaborator
DNV GL | Marek Wasilewski | Architect
DNV GL | Jens Eftang | Developer
DNV GL | Lars Peder Amlie | Developer
Microsoft | Justin Bronder | Principal SDE
Microsoft | Olav Tollefsen | Principal Technical Evangelist
Microsoft | Anders Gill | Technical Evangelist


## Tools used during the hackfest:

* Microsoft Azure
 * Storage Blobs
 * Azure ML Studio
 * Azure Notebooks (Jupyter/IPython Notebook)
* Azure Storage Explorer
* Microsoft Excel
* Visual Studio 2017 RC
* FME Desktop 2016

## The process

The project lasted for a period of five days (Monday to Friday), with a presentation of the results in the morning of day five. This meant that the team had four full days to complete the task of;

1.	Understanding the data
2.	Cleaning the data
3.	Building the model
4.	Evaluating the model
5.	Optimizing the model
6.	Creating a web service
7.	Integrating the model

## Understanding the data

Step 1 (understanding the data) meant discussing each and every column that came from the data source (Spatial GIS DB). This requires domain knowledge and we were lucky that we had highly skilled DNV GL representatives on sight to explain what each and every column meant and how it would relate to the big picture.
On Monday, we set the goals for the whole hackfest. 

We created the appropriate Azure accounts, created a resource group, a storage account, an AML (Azure Machine Learning) Workspace and distributed access. We downloaded the necessary tools and created directories for each day in the storage blob. We uploaded the raw dataset exported from the FME Desktop ETL (Extract Transform Load – used by DNV GL) tool into the storage blob and started to go through which columns we would keep and which ones we would discard. We discussed whether we should incorporate external data sources from AccuWeather (or USDA – US Department of Agriculture). We discussed multiple algorithms (like binary classifiers) and planned how we should parallelize the work (splitting the work).

### Highly motivated team

[TEAM]

## Cleaning the data

Since we used day one of the hackfest to get a better understanding of the data, we were ready to move on to the preprocessing stage of the hackfest. This stage turned out to be the most time-consuming stage of the whole hackfest (which is to be expected when working with data). There are multiple ways of how you can clean the data. We already knew that we were going to use the designer in AML Studio for the making of the machine learning model, and we also wanted to leverage more aspects of the package (like the Jupyter notebooks which works as an integrated part of AML Studio). If we could split the work where we did some of the preprocessing in AML Studio but mostly in the Jupyter Notebook to learn and expand our knowledge; that would be the most optimal strategy for our application (mixing both worlds). We decided to go for that approach and learn Python with the use of the Pandas framework for preprocessing of the data. 

Pandas is an open source, BSD-licensed library providing high-performance, easy-to-use data structures and data analysis tools for the Python programming language. Since Jupyter notebooks is an integrated part of the AML Studio, there were no issues in creating a Jupyter IPython Notebook and performing the cleaning tasks within this notebook. We loaded the dataset from the Azure Storage Blob, did all our data cleaning and saved the file back into Azure Storage Blob. Jupyter notebooks with pandas proved to be extremely valuable and really helpful for us as it was versatile and consisted of all the functions we needed to perform our tasks. This is definitely something we will continue on using and encourage others to use as well for their own cleaning tasks in their respective projects.

We have created a public repository with three Jupyter IPython Notebooks that consists of documented python code which [shows the true usefulness of the pandas framework](https://github.com/readyforchaos/Pandas-transform).
(note: I have deleted the storage account name and key. You need to insert your own account name and key in order to connect to your storage blob in Azure). 

We started off with more than 300 columns (features) but eventually ended up with “only” 22 features and 60 882 observations of data (rows) after the cleaning. We decided to drop a lot of features so that it wouldn’t clutter the algorithm and to make sure it focused on the important features rather than obsolete ones that don't have any predictive power (based on intuition and the domain knowledge of the people at DNV GL).

An example of how we leveraged the pandas data frame structure to calculate the mean for a data frame column without including data that consisted of -999 or were NULL.

```python
mean_wallthickness = df[(df.WALLTHICKNESS != -999) & (df.WALLTHICKNESS).notnull()].WALLTHICKNESS.mean()
```
We then used this variable to replace all -999 and NULL occurrences with the mean wall thickness that was calculated above.






