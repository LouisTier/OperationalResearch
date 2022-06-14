# Operational Research : Multiple-criteria decision analysis

## **1. About this project**

Everything is explained in the pdf file named "**ProjectReport**". However, as it is written in French, this README file will explain the main points in English.

The objective of this project is to answer the problem of a company, here **SCNF (1)**. We come to compare different alternatives on different criteria to finally decide which solution is the best for us. In other words, we try to **choose which vehicle is to be favored according to the conditions** imposed by the subject.

We are faced with a strategic problem, hence the need for this **MCDA method**. Here we try to help our decision-maker: SNCF which is an industrialist.
In this subject, we have **5 alternatives** at our disposal: 
  - VE DE
  - VE EU 27
  - VE FR
  - VT Gasoline NEDC 
  - VT Diesel NEDC
We have here several options, namely an *electric vehicle* or a *thermal vehicle*.

Behind this study, we try to **establish a classification of the given vehicles** to give a final recommendation to the decision-maker according to several criteria of comparison criteria that he will have given us. 

The goal is to **minimize the different environmental impacts of these vehicles** (energy balance, greenhouse gas emissions, etc.) and to choose the most appropriate one.

To compare the alternatives, we rely on many **evaluation criteria**:
  - CC (climate change)
  - AC (acidification)
  - Eutro (Eutrophication)
  - CED (Total Primary Energy)
  - Dec rad (radioactive waste)
  - Em rad (Radioactive emissions to air)
  - Nox (NOx emissions).
The experts who will evaluate these alternatives are **members of ADEME**, which is leading this study.

For the MCDA we have to choose a method. 
ELECTRE I identifies a set of solutions while ELECTRE III ranks a set of solutions from best to worst - although it requires more computation than ELECTRE I.

In addition, ELECTRE III **takes into account the preferences associated with the judgment criteria**. It is through a weighting step that the different actors can give their opinions and express possible differences in judgment - Simos' method. We, therefore, **choose the ELECTRE III method**.

## **2. SIMOS method: calculation of indicator weights**

We first evaluate the impact of the indicators using the SIMOS method.
The decision-maker has previously sorted the criteria in the order of increasing importance that he prefers. 
He can also add "**white cards**" between the criteria if he considers that **one criterion is much more important** than the important than the next one.

From this ranking, we calculate the non-normalized and then normalized weights of the criteria to finally obtain the following weight table: 

![image](https://user-images.githubusercontent.com/105392989/173569132-bbab417e-7596-4282-bfce-267244a757cc.png)


## **3. Credibility matrix**

To obtain the **"overall" credibility matrix**, this method and these calculations must be repeated for each of the alternatives - a total of 5 times.
The first step is to calculate the delta of each criterion between VE DE and all other alternatives.

![image](https://user-images.githubusercontent.com/105392989/173569241-7e814adb-e22e-47ee-b547-30cbec2cc0bd.png)

In order to determine the partial match indices, we need to determine the **thresholds for each criterion and each alternative**, namely 
  - Preference threshold
  - Threshold of indifference
  - Veto threshold

![image](https://user-images.githubusercontent.com/105392989/173569649-b5944a47-eca2-49fa-b4f5-b02779033873.png)

Following this, we can obtain the **partial concordances** in order **to deduce the global concordance** of a given alternative. Here is an example of the global concordance obtained for the alternative VE DE :

![image](https://user-images.githubusercontent.com/105392989/173570231-321150ad-d9f2-4d5e-98a8-de08619864a4.png)

Subsequently, we are interested in the global discordance. For that we also pass by the **partial discordance** and a **set called F** defined as follows: 

![image](https://user-images.githubusercontent.com/105392989/173570556-a41ba73c-201d-43f7-bec7-1401585f7811.png)

*where 'a' represents our alternative era and 'b' a second alternative to which we compare it.
d' represents the partial discordance and 'c' the global concordance.*

After having obtained this **global discordance**, we can finally obtain the last parameter which will be useful for the final classification, namely the **credibility index** defined as follows: 

![image](https://user-images.githubusercontent.com/105392989/173571553-6a432a1b-f268-448b-8c4f-8a2de5907eb8.png)

After repeating these steps for each of our alternatives, we obtain the following **credibility matrix**: 

![image](https://user-images.githubusercontent.com/105392989/173571803-30e820df-5dcf-4680-8e9d-7f477d95834d.png)


## **4. Final ranking**

In order to obtain the final ranking, it is necessary to use **two distillation algorithms distillation** - one ascending and one descending. Indeed, with ELECTRE III, the relationship of relationship becomes blurred when we introduce the concept of **pseudo-criteria**: *a outranks b in the measure of ρS(a, b)*.

To obtain the outranking relation S, a threshold λ, called *λ-cut* or *λ-threshold*, is introduced:

![image](https://user-images.githubusercontent.com/105392989/173573048-b7f02e2a-daff-4906-9e6b-c7ed97978cb7.png)

We obtain a structure from this binary outranking relation (aSb) with some preference (P), indifference (I) and incomparability (R).
So we start from our credibility matrix and obtain the following relations: 

![image](https://user-images.githubusercontent.com/105392989/173573240-95415988-c4d3-400d-8895-6f2b0fb88ffc.png)

  **1. Case 1: The top-down ranking algorithm**
  
  ![image](https://user-images.githubusercontent.com/105392989/173573623-cd01daa0-593e-4115-9551-56719a2b4ca1.png)

  First, we start by establishing the λ-cut for the first step of the algorithm (k = 0) : 
  
  ![image](https://user-images.githubusercontent.com/105392989/173573788-b897d7de-3bf5-4e4b-a5fb-7e1944bb2285.png)

  After determining the λ-cut, we determine os, od and q :
  
  ![image](https://user-images.githubusercontent.com/105392989/173573911-e2ce6ec7-ab78-43cc-bbcb-8fe806911c37.png)
  
  We recover and rank in decreasing order the alternatives selected at each step -alternative **where the q is maximal**.
  Once this is done, the alternative is removed from the table and the procedure is **repeated until there are no alternatives left**.
  We obtain the final ranking: 
    - CC (climate change)
    - Rank 1 = VT Gasoline NEDC
    - Rank 2 = VE DE
    - Rank 3 = VT Diesel NEDC
    - Rank 4 = VE EU 27 and VE FE

  **2. Case 2: The bottom-up ranking algorithm**
  
  ![image](https://user-images.githubusercontent.com/105392989/173573674-606a0382-757e-437d-b071-f301b0916ca3.png)
  
  Here the principle is exactly the same as for the top-down algorithm. The only difference is that we recover the alternatives **where q is minimal**. 
  We therefore rank in **ascending order**.
  
  We obtain the following ranking:
    - Rank 1 = EU 27 EV and VT Diesel NEDC
    - Rank 2 = VE DE
    - Rank 3 = VE FR and VT Gasoline NEDC
    
In order to obtain the final ranking, we need to **"merge" the rankings of the two algorithms**.
To do this, we will construct the preference (P), indifference (I) and incomparability (R) sets defined as follows incomparability (R) defined as follows:

![image](https://user-images.githubusercontent.com/105392989/173575597-eef13a1b-4333-4289-8cb7-3c4024d63691.png)

The final classification obtained through this merger is therefore :
  - **Rank 1 : VT Gasoline NEDC**
  - **Rank 2 : VE DE and VE FR (incomparable)**
  - **Rank 3 : VT DIESEL NDEC**
  - **Rank 4 : VE EU 27**


## **5. Interpretation and recommendations**

From the final ranking, we deduce that the **NEDC Gasoline thermal vehicle is the best alternative** among the 5 proposed according to the criteria and the weighting of the SNCF 1 decision-maker to minimize the environmental impact induced by the vehicles. 
However, the fact that here the thermal vehicle is better than an electric vehicle **is by no means a generalization**. In fact, in second place, there are two electric vehicles, ahead of another combustion vehicle: VT Diesel NEDC. 

Moreover, the **weighting of the criteria plays a crucial role** in the ranking. 
Today our decision-maker has proposed such importance among the criteria but maybe in 5 years, the weighting will vary according to the needs of the moment, the philosophy of the decision-maker, and according to many factors. And once this new weighting is done, and certainly according to new thresholds, the **result will be completely different**. 

Moreover, here only one aspect has been taken into account: the environmental aspect. However, to push the study and the choice of the vehicle a little further, it could be interesting to look at two other aspects:
  - **Economy: does the decision-maker want to favor profits?**
  - **Society: does the decision-maker want to please the population?**

Once the rankings have been obtained in these three respective aspects, we can again propose a weighting system according to the strategy of the decision-maker and thus propose THE vehicle to best satisfy these three aspects.
It is therefore essential for the decision-maker to **always check and update his strategy and his criteria to determine the best alternative**.

This example clearly shows the interest and power of operational research. Indeed, with such a multitude of criteria, it is **difficult to choose first sight**.
