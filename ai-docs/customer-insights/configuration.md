---
title: "Preview: Configuration | MicrosoftDocs"
description: Text to go here
ms.custom: ""
ms.date: 10/1/2018
ms.reviewer: ""
ms.service: "dynamics-365-ai"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "Dynamics 365 (online)"
  - "Dynamics 365 Version 9.x"
ms.assetid: 
caps.latest.revision: 31
author: "jimholtz"
ms.author: "jimholtz"
manager: "kvivek"
robots: noindex,nofollow
---
# Configuration

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

> [!IMPORTANT]
> - This feature currently has limited availability.
> - [!INCLUDE[cc_preview_features_definition](../includes/cc-preview-features-definition.md)]  
> - [!INCLUDE[cc_preview_features_expect_changes](../includes/cc-preview-features-expect-changes.md)]  
> - [!INCLUDE[cc_preview_features_no_MS_support](../includes/cc-preview-features-no-ms-support.md)]  



## Configure Data

### Intro to Configuration
Once ingested your data, you are ready to unlock the unique data-configuration features that Customer 360 offers. **Configure Data** includes four modules as represented by the tiles at the screen below and you should explore these from left to right. The goal behind the Data Configuration process is to unify datasources that once were disparate into a **"master customer dataset"** that includes a more complete and accurate information on your customers than the original datasets.  

### Map
Clicking the **Map** tile at the **Configure Data page** will take you to the first stage in the data configuration process. 
[]

There are two main goals behind the Map page that is shown below:
- Entity selection: Identifying the customer entities which, upon unification, may lead to a dataset with a more complete information on your customers
- Attribute selection: For each customer entity, identifying the columns upon which you will want to combine your data in the next phase (those columns are also called **Attributes**)

![map-screen1.png](media/map-screen1.png)

Clicking each of the customer entities tabs on the left will open it's corresponding attributes table. Below we will explore each of this table's columns, going left to right:
- **Primary Key:** For executing the identity-resoultion process it's mandatory to **select one attribute as a unique key** for each of the customer entities. For example, if one of your data sources is a *Contacts* dataset, you may want to assign *Customer Name* as the unique key for that source, while for a *Call-Logs* file you may prefer to define *Phone Number* as a unique key. 
- **Name**: The attribute name
- **Type:** Categories under which your attributes fall such as email or name. Adding a custom entity type is also possible: Upon clicking the type for a given attribute and selecting **Custom** you will be able to type your custom type
- **Normalize:** Optional column. Here you can select whether and how to normalize all the data that you use for the matching process. Several options are available such as removing whitespaces, normalizing digits, removing punctuation, and others. 

In addition, three additional actions are available in the Map page:

![add-custom-entity.png](media/add-custom-entity.png)

- **Add customer entity:** Available upon clicking the **Add** drop-down menu (shown below). If you think there are additional entities on the basis of which your data should be merged, you should add them at this point.
    - Using the customer entities panel (shown below), first you want to click on the data source from which you wish to add more customer entities. In the example below, clicking the *Dynamics* data source opened a list with all the entities for that source. You may also use the search button to find a specific entity.
    
    - Next, you want to select the entities that you want to add. In the example below (right image) few entities have been selected.

      ![add-entity.png](media/add-entity.png)

    - Lastly, you want to save your selection and now these will be added as new tabs to the left of the entity table. 
      
      ![add-entity2.png](media/add-entity2.png)
- **Add attributes to an existing customer entity:** Available upon clicking the **Add** drop-down menu (as shown below). Choosing this option for one of your customer entities will enable you to take more attributes into consideration as part of the matching process. [UX is not ready for selection panel]

![add-attribute.png](media/add-attribute.png)

![add-attribute2.png](media/add-attribute2.png)

- **Keep unmatched records:** As part of the next stage (match), it is possible that not all of your data entities will be matched. Upon checking this box (shown below), you choose to save all the records (or dataset rows) of your unmatched entities in your master data profile for future use. This option is recommended if.. [(to complete)] 

> [!div class="mx-imgBorder"] 
> ![](media/map-keep-unmatched-records.png "Mapping - keep unmatched records")

### Match
Once mapping is completed, you are ready to match your mapped entities. Clicking the *Match* tile in the *Configuration page* will take you to the *Match page*.

![match-tile.png](media/match-tile.png)

In the *Match* page below, some matches were already automatically identified based on your Map phase selections. However, since there are many ways and orders by which customer entities might be matched, this phase enables you to specify the match logic that best resonates with:
- Your understanding of how your datasources are related to one another
- Your understanding of what sources are most reliable for your mapped attributes

![match.png](media/match.png)

### Exploring the Match page
The *Match* page includes two major sections: **Summary** and **Details** as explored below. Above these components you will find three tiles that specify your total number of customers (right tile), total number of customers for which information has been already matched (left **Matched Customers** tile) and total number of customers for which data had not been matched yet (center **Unmatched Customers** tile).   

#### Summary Section
This diagram visualizes the hirarchy by which your ingested entities are currently matched. Each of the entities is represented by a tile with the entity's name, the datasource from which it was dervied, number of records, end possibility to view those records by clicking the button at the bottom-right corenr of the tile.                                

To examplify the logic that is captured in the **Summary** part, the following matching sequence is reflected in the diagram below:
- First, *Sales Data* from *Salesforce* will be matched with *Sales Data* from *Dynamics 365*
- Then, the matched dataset that resulted from step one will be matched with *Survey Data* from *Salesforce*
- Then, the matched dataset from step two will be matched with *Solication Data* from *Salesforce*
- Lastly, the matched dataset from step three, will be matched with another *Sales Data* dataset from *Salesforce*
    
[]

In addition to entities, the Suammry diagram includes three types of status for the different matchings. Those are stated on top of the links that connect each matching pair. 
- In the example above, all these links have the same status: **Rules Needed**. This status implies that no rules were defined for the match pair. As we will see, at least one rule **must** be added to each of the matchings and it can be done in the **Details** section
- Once rules were defined for a given match pair, it's status will turn to **Ready to Run**. As we will see, running a match is also available within the **Details** section. 
- **Matching** is the third status you can see for a given match pair. This status implies that the matching process is currently under progress (reflected as a percentage).   
- **Complete** is the forth and last status you can see for a given match pair and it reflects the completion of the matching process both for this matching and for all the matchings that precede it. In the example shown below, the first two matchings were completed while the third matching is under progress:

[]

- **Adding and Editing Match Pairs**
Both actions can be done by clicking the **Edit** botton:

[]

Upon clicking it, the following panel opens up:

[]

Each match pair occupies one row in this panel. 
- **Adding a new a match pair:** Click the **Plus Sign** that is highlighted in the image above. Then choose the two entities that will be included in the new match pair. 
- **Editing a match pair's entities:** Upon clicking a match pair entitiy you will be able to change it to any of the other entities
- **Changing the order by which matches are executed:** That can be done by replacing a given row's values with another row's values. In the example above, in order to switch the order of the first match pair () and the second match pair (), we will need to replace the entities in the first match pair with those of the second match pair and vice versa. 

#### Details Section
This section captures your matchings in a table. Let's explore the **Details** table fields, going left to right:
   - The first column specifies the order by which the matchings will take place (reflecting the same sequence as in the summary part)
   - The next two columns specify the specific match pair members, whether these are single entities (highlighted in blue in the example below), or datasets resulted from prior matchings (highlighted in red in the example below).
   - The next two columns specify the number of matched and unmatched records **for that specific matching** 
   - The last column includes a status circle: This circle is checked once a match pair is in **Complete** status (as explained above)

Next to these fields you will find a **three dots icon**. Clicking it will enable you to perform the following actions:
- **Running a match pair**. Clicking **Run** will run the specific match pair you are hovering over. For running all your match pairs at the same time, go to the bottom of the Match screen and his the **Run All** button.
- **Adding and Editing Match Pair Rules:** Clicking **Edit** will open the **Edit Match Rule** pop-up window:

[]

Besides the role name, this panel enables you to specify all the ***Criteria*** for that role. Each Criteria is represented by a row that includes (going left to right):
- The attribute that will be used for matching within the first match pair entities
- The attribute that will be used for matching within the second match pair entities
- The method used for that criteria where selecting ***Exact*** will dictate that only matching records will be matched and selecting ***Fuzzy*** will dictate that records that are not 100% matching will also be matched. The threshold for Fuzzy matches will be selected next to it: You can define these as either *Low*, *Medium* or *High*.
- An either *OR* or *AND* operator where:
  - *AND* states that the criteria will be executed together with the next criteria
  - *OR* states that either this or the next criteria should be executed

![match-edit-rule.png](media/match-edit-rule.png)

 
### Merge
This is the last step within the data configuration process and it's all about reconciling conflicting data. Examples for such a conflicting data might be the customer name which resides in two of your datasets but shows a little bit different (Grant Marshall versus Grant for instance), or a phone number format that slightly differs (617-8030-91X versus 617803091X for instance). Merging those conflicting data points is done on a attribute-by-attribute basis as detailed below.

- **Viewing pre-identified merged attributes**: These attributes are shown under **Merged Attributes** in the highlighted page part below. In this example, the attribute *Name* was selected and the table shown includes all the values that were found for that attribute within all the customer entities. Moreover, a specific attribute value (for example the name *Grant*) can be searched for using the ***search icon*** above the values table. Lastly, note that you can also view all the attributes that were *not* used as part of the Merge process - those appear under **Unmerged Attributes** in the left-bottom part of the screen.

![merge-single-attribute.png](media/merge-single-attribute.png)

- **Prioritizing sources for pre-identified merged attributes**: Continuing with *Name* as an example for merged attribute, in this section we will learn how to prioritize contradicting values for that attribute. We start by selecting <b>...</b> below: 

![merge-single-attribute-edit.png](media/merge-single-attribute-edit.png)

- We will conduct the prioritization process within the **Edit Attribute Panel** as shown below. This panel consists of three parts: *Attribute Name* (upper part), *Attribute Source* (middle part) and *Merge Policy* (lower part). 

![merge-experiment-datasource-dropdown.png](media/merge-experiment-datasource-dropdown.png)

  - First we will consider to edit the *Attribute Source* part. This part specifies all the sources that include values for the *Name* attribute. we can see that by default, all these sources are selected and hence values for the *Name* attribute are taken into consideration from all three sources. If we wish **not** to consider one or more of the sources we will unselect them.
  
  - Second, we will consider to edit the *Merge Policy* part. This part specifies only the sources that were selected within *Attribute Source*. Here we will prioritize those sources: If we think for example that *Dynamics WiFidata* includes the most accurate data about *Names*, than in the panel shown above, we will click the arrow sign next to *Salesforce Sales Data* and as a result *Salesforce Sales Data* will move to first priority while *Dynamics WiFidata* will move to second priority when pulling values on *Names*.

- **Adding a merged attribute**: Adding a merged attribute is available via the *Add Attribute* option as shown below. 

> [!div class="mx-imgBorder"] 
> ![](media/merge-add-merge-attribute.png "Add merged attributes")

- We will perform the attribute addition process within the *Add Attribute* panel as shown below. This panel consists of three parts: *Attribute Name* (upper part), *Select Attributes* (middle part) and *Merge Policy* (lower part). 

![merge-experiment-datasource-dropdown.png](media/merge-experiment-datasource-dropdown.png)

  - First we will type an attribute name in the *Attribute Name* field. This is the name we are giving to our merged attribute.
  - Then, within the *Select Attributes* menu, we will select all the attributes that we want to merge into our specified attribute.
  - Lastly, we will define the merge policy by clicking on the relevant arrows in the *Merge Policy* section as we did before.
  
- **Editing a group merged attribute**: In some cases, it will be valuable to group multiple attributes as one merged attribute. In the example shown below, the attribute *Address* is defined as a group attribute as represented by the icon next to it (such icon doesn't appear next to single attributes). The table shown includes all the attributes that are included in the group attribute.
  
![merge-group-attributes-dropdown.png](media/merge-group-attributes-dropdown.png)

   - In order to edit a group attribute, we will click on the *three dots* icon just as we used to do for a single attribute.
   - In the next stage, we will use the *Edit Group Attribute* panel that is shown below. We want to find all the attributes that should be included in this group attribute and we will achieve that by typing those attributes names in the *search* field.
     
 ![merge-group-attributes-edit.png](media/merge-group-attributes-edit.png)
 
 
