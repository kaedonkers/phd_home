# Kevin Donkers' PhD
Welcome! This is the landing page for my PhD research. On it you will find an overview of my PhD, outlines for my (proposed) projects and presentations about my work.
Additionally you will find links to other repositories used for this PhD.


## PhD details

I am doing this PhD as part of the Environmental Intelligence CDT* at the University of Exeter, UK.
This PhD is financially supported by the Met Office, to whom I am very grateful.
I started this PhD in September 2020 and, due to the part-time nature of it, have a finish date of September 2026.

My supervisors are [Prof. Brett Day](https://business-school.exeter.ac.uk/about/people/profile/index.php?web_id=Brett_Day)$^1$, 
[Dr. Daniel Williamson](https://mathematics.exeter.ac.uk/staff/dw356?sm=dw356)$^1$ and 
[Dr. Deborah Hemming](https://www.metoffice.gov.uk/research/people/deborah-hemming)$^2$.

*CDT = Centre for Doctoral Training<br>
$^1$ University of Exeter, UK<br>
$^2$ Met Office, Exeter, UK


## Overview
As part of the UK Government’s Net Zero targets, tree cover of a significant proportion of the UK’s land area needs to increase over the coming decades. Given that 70% of the UK land area is used for agriculture these trees will replace some agricultural production. This has the potential to impact Britain’s food security, particularly under a changing climate. Therefore is it crucial that we have evidence to support the right land use decisions being made now. The current strategy focuses on a “land sparing” approach - planting large areas of woodland while intensifying agriculture on the remaining land. Agroforestry, integrating trees into agricultural production systems, represents a “land sharing” approach and has the potential to be a more resilient system of planting trees while retaining food production capacity. The focus of my research, therefore, is to understand how these two approaches can be implemented to maximise carbon sequestration, food production and other ecosystem services.

The challenges for this research are threefold. Firstly, there is little empirical data on agroforestry in the UK. There are a very small number of long running experiments but not enough to be representative of the whole UK. This is where agroforestry modelling is useful. Agroforestry models can simulate multiple configurations of land use in a much shorter time than experimenting in the field. However, they can be computationally expensive to run. Model emulation, a statistical approximation of a model, can reduce the runtime of these models. This could be crucial for optimising these models for carbon sequestration as such techniques require iteration over multiple model runs. 

The second challenge is factoring climate change into an assessment of agroforestry potential. I will quantify how these models respond to the uncertainty inherent in climate change projection data and use it to determine how resilient different land use configurations are to future climates. Using techniques such as integrated Gaussian processes to emulate the models can achieve this uncertainty quantification.

The third challenge explores how agroforestry will be adopted. A physical understanding of what combination of land use types leads to optimal natural capital doesn’t mean that it is desirable or even possible to implement. Therefore an assessment of policy options is needed. I will use techniques such as agent based modelling and decision theory to simulate how different incentives affect the uptake of tree planting in a way that maximises carbon sequestration but also food security. 



## Research questions

1. How can agroforestry be modelled at scale in a UK context?
2. How does a land-sparing (agriculture+forestry) approach to tree planting compare to a land-sharing (agroforestry) approach, when analysed at scale?
3. How does uncertainty propogate from input data (e.g. climate variability) and other sources (e.g. model descrepency) through a scaled-up agroforestry model?
4. How to use results, with uncertainty quantification, to assess tree planting strategies for different risk appetites?


## Methods

### Data

#### **Agroforestry data**
Collated from literature and field studies. Collaborating with [Prof. Paul Burgess]() on this.
Extent, quality and completeness of data still to be assessed.


#### **Climate change data**
UK Climate Projection 2018 ([UKCP18](https://www.metoffice.gov.uk/binaries/content/assets/metofficegovuk/pdf/research/ukcp/ukcp18_headline_findings_v4_aug22.pdf)) data are a collection of gridded ensemble simulation outputs for the UK climate up to the year 2080. Data is available for the RCP8.5* climate scenario at 60km, 12km and 2.2km spatial scales, and daily, monthly and annual timescales. 

[CHESS-SCAPE](https://catalogue.ceda.ac.uk/uuid/8194b416cbee482b89e0dfbe17c5786c) is a downscaling of UKCP18 to 1km spatial scale and additional RCP scenarios, performed by the UK Centre for Ecology and Hydrology (UKCEH) as part of the Climate Hydrology and Ecology Research Support System ([CHESS](https://catalogue.ceh.ac.uk/documents/7de9790e-66a2-44b5-988e-283d764ef52f)). It was designed to drive higher resolution land-surface models, such as the Joind UK Land Environment Simulator ([JULES](https://jules.jchmr.org/)).

The daily, coarse 12km resolution regional climate version of UKCP18 is being used for development purposes with the agroforestry model in this PhD, but the aim is to use the 1km high resolution CHESS-SCAPE data once the model performance and experimental design has been finalised. However, there are now only 4 ensemble members rather than the 12 of the original UKCP18.

CHESS-SCAPE data is now available on CEDA's data archive:<br>
https://data.ceda.ac.uk/badc/deposited2021/chess-scape/data


*RCP = Representative Concentration Pathway

#### **UK soil data**
Soil data acquired from a collaborator in the [Net Zero Plus]() project, source unkown.


#### **Other data**
Other potentially useful data could be land cover data to exclude areas of the UK which are unsuitable for agriculture e.g. urban areas, existing forestry, nature reserves, etc.



### Agroforestry model
After a literature review on agroforestry modelling, I chose [Yield-SAFE]() for this investigation. It is a parameter-sparse, biophysical, mechanistic model which simulates biomass accumulation of co-located trees and crops. It requires only daily meteorological data and parameters describing the soil, tree and crop properties being simulated. 


### Bayesian model calibration
The plan is to follow an approach of based on [Kennedy & O'Hagan, 2002, *Bayesian calibration of computer models*](https://doi.org/10.1111/1467-9868.00294) with guidance from [Lambert, 2018, *A Student's Guide to Bayesian Statistics*](https://uk.sagepub.com/en-gb/eur/book/student%E2%80%99s-guide-bayesian-statistics#description). This is likely to require many thousands of model executions with a Monte Carlo based method, so the model should either be fast or emulated.




