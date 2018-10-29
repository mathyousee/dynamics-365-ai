---
title: "Get data| MicrosoftDocs"
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
# Get Data

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Follow these steps to start loading data from your data sources.

## Step one: Creation

Select **Get Data** to open the Dataflow page as shown below. You can consider dataflow to be a resource pool that is created in the system for your application usage.

- **If it’s the first time you are using Customer 360** you need to create a dataflow, and that is available through the highlighted **Add Entity** button:

[add image 2b]

Then you should give your dataflow a name and possibly a short description as shown below:

> [!div class="mx-imgBorder"] 
> ![](media/connection-settings.png "Connection settings")

Lastly click your new dataflow to start ingsting entities into this dataflow.
- **If it’s not the first time you are using Customer 360**, you should use this screen to either selecting a dataflow you have created in the past or creating a new one. 

- **Step Two: Identifying Data Sources**: Within the datasources page that is shown below you should locate the specific sources that apply to your organization. First identify their types which are represented by the tabs at the top of the page (highlighted below). Then, search for your specific sources under the relevant tabs.

> [!div class="mx-imgBorder"] 
> ![](media/choose-data-source-menu.png "Data source menu")

Lastly, upon clicking a datasource that you wish to ingest, you will need to complete all the required fields for that datasource. An example for Excel (.csv) file mandatory fields is shown below. Once all field are filled, approve by selecting **Next** at the bottom of the page. At any point you can also remove a datasource from your dataflow **by clicking the dataflow and then ?**.

[4]

- **Step Three: Editing Entities**: You can edit any entity that you have ingested in step two. In order to edit an entity:
    - First click the entity that you wish to edit
    - Then click **Edit Entity** as shown in red below. Note that this screen is where you can also refresh an entity's data (as highlighted in blue below):
    
[5]
    - Lastly, you will use the **Power Query** editor that is shown below for the editing process. Editing columns, combining tables, and several other useful functionalities are available in the top screen menu (as shown in red below):
    
[6]
     
If you are new to power query, you might want to spend a couple of minutes on the following documentation that will walk you through these functionalities:
[link1]

-	**Step Four: Dataflow Refresh:** Once finishing selecting data sources, you will get back to the dataflow screen. The final step is to hit the **Refresh** button as shown below:
[7]

Note: In the future this step will happen automatically. 

### Next Step: 
Now you are ready to unlock unique customer insights through the **Data Configure** sections (those include **Map**, **Match** and **Merge**). If you wish to review all the entities that were ingested as part of the **Get Data** process, review the **Entities** section first. 
