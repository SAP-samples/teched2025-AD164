[Home - AD164@SAP TechEd 2025](../../#exercises)

# Getting Started

## Overview 

**Table of content***
- [Create a connection to the ABAP system in ADT](#create-a-connection-to-the-abap-system-in-adt)
- [Solution Packages](#solution-packages)
- [Group ID (Suffix)](#group-id-suffix)
- [Your Exercise Package](#your-exercise-package)
- [Helpful Information](#helpful-information)
- [Summary & Next exercise](#summary--next-exercise)

> [!NOTE]    
> The screenshots in this document have been taken using the suffix or assigned suffix  **`810`** and the system **`D23`**.  
> We **do not recommend** using assigned suffix **`810`** or **`000`**.
> 
> Please note that ADT dialogs and views as well as SAP Fiori UIs may change in upcoming releases.

## Create a connection to the ABAP system in ADT

Complete one of the options below to connect your ADT client to the ABAP backend:
- Option 1 — if you are working on **SAP S/4HANA** or **SAP S/4HANA Cloud Private Edition**.
- Option 2 — if you are working in the public cloud, on **SAP BTP ABAP Environment** or **SAP S/4HANA Cloud Public Edition**.

> [!IMPORTANT]  
> Use **Option 1** for the hands-on workshops at **SAP TechEd Berlin 2025** and **ASUG Tech Connect 2025**. 
  
### Option 1: Create an ABAP Project in ADT

> Complete the steps below in ADT if you are working on **SAP S/4HANA** or **SAP S/4HANA Cloud Private Edition**.

<details>
  <summary>🔵 Click to expand!</summary>
   
1. If not done already, open the **ABAP** perspective as shown in the screenshot below.

   ![Open ABAP Perspective](images/abap_perspective.png)

2. If not done already, now create the **ABAP Project** as shown in the screenshots below. 
  
   Maintain the system info and user credentials, and confirm.

   ![Create ABAP Project 1/2](images/abapproject_systemlogon1.png)
    
   You can keep the default **_Project name_** and click **_Finish_** to create the new ABAP Cloud Project in the **_Project Explorer_** view. 

   <!--![Create ABAP Project 2/2](images/abapproject_systemlogon2.png)-->

</details>


### Option 2: Create an ABAP Cloud Project 

> Complete the steps below in ADT if you are working on **SAP BTP ABAP Environment** or **SAP S/4HANA Cloud Public Edition**.
 
<details>
  <summary>🔵 Click to expand!</summary>
   
1. If not done already, open the **ABAP** perspective as shown in the screenshot below.

    ![Open ABAP Perspective](images/abap_perspective.png)

2. If not done already, now create the **ABAP Cloud Project** as shown in the screenshots below. 
  
   For **step 4** in the screenshot below, you will either import or copy and paste the 🔑 **service key** of the SAP BTP ABAP environment system on which you'll be performing the exercises. Then click **_Next_** to continue.

    ![Create ABAP Project Cloud 1/2](images/steampunk_systemlogon1.png)
  
   For **step 7** in the screenshot below, use the email and password of your ABAP user to log in to the system.
  
   You can keep the default **_Project name_** and click **_Finish_** to create the new ABAP Cloud Project in the **_Project Explorer_** view. 

    ![Create ABAP Project Cloud 2/2](images/steampunk_systemlogon2.png)

</details>

## Solution Packages
[^Top of page](#)

Participants of SAP-led events, such as on-site SAP TechEd 2025 events, will find the solution packages **`ZAD164_SOLUTIONS_CLASSIC`** and **`ZAD164_SOLUTIONS_ABAP_CLOUD`** in the dedicated SAP S/4HANA system provided by SAP. You can take a look at the solutions, before you start with the implementation in your assigned exercise package. 

<details>
  <summary>🔵 Click to expand!</summary>

**Classic ABAP: Classic ALV-based _Manage Travels_ app:**

- Package name: **`ZAD164_SOL_ALV`**
- Program (Report): **`ZAD164_REPORT_CLASSIC_ALV`**

<details>
<summary>🖼️Click to expand!</summary>
<img src="../images/travelapp_alv_sol01.png" alt="Classic ABAP - Manage Travels Ap" width="100%"> 
</details>

**ABAP Cloud: RAP-based _Manage Travels_ app:**

- Package name: **`ZAD164_SOL_RAP`**
- Service binding: **`ZAD164_UI_TRAVEL_O4_RAP`**

<details>
<summary>🖼️Click to expand!</summary>
<img src="../images/travelapp_rap_sol01.png" alt="ABAP Cloud - Manage Travels App" width="100%"> 
</details>

**ABAP Cloud: RAP-based _Manage Travels_ app (extended version):**

This version of the _Manage Travels_ app includes various RAP capabilities, that are not covered in the exercises due toi time restrictions.

- Package name: **`ZAD164_SOL_RAP_EXT`**
- Service binding: **`ZAD164_UI_TRAVEL_O4_EXT`**

</details>


## Group ID (Suffix)
[^Top of page](#)

In this exercise step, you will define a group ID, which will be use as **suffix** throughout this workshop to uniquely identify your repository artefacts and distinguish them from those of other users working on the same system.

> [!NOTE]  
> Attendees of **on-site SAP-led events**, such as SAP TechEd 2025, will be assigned a group ID by the SAP team, which should be used as **suffix**. They can therefore skip this section and proceed directly with the next one: _Your Exercise Package_.

<details>
  <summary>Click to expand!</summary>
   
As the ABAP environment is used by many people, we've defined a naming pattern for each artefact you are going to create to make sure it doesn't conflict with other ones. 
  
For this, you'll find the placeholder **`###`** used in object names that must be replaced with the group ID of your choice during the exercises. 
  
The group ID can contain **a maximum of 3 characters (numbers and/or letters)** - e.g. `123`, `XY1`, or `ABC`. 

You can check for **already used group IDs** by choosing **Open ABAP Development Object** ![open_object_icon](images/adt_open_object.png) or pressing **Ctrl+Shift+A**, and searching for e.g. **`zad164_*###`**, where **`###`** is your chosen suffix. All artefacts fitting that pattern will be listed.  

Try to add e.g. your initials, followed by a number to verify nobody else is already using this group ID. 

In the screenshot below, we're checking to see if the suffix **`###`** is still available, so we enter **`zad164_*###`** as search string.

_**No results**_ means this group ID  seems to be available. You can note it as your group ID somewhere and use it in the next exercises.

Once you've found an available group ID, choose **Cancel**.

<img src="images/groupid01.png" alt="determine group id" width="40%">

</details>

## Your Exercise Package
[^Top of page](#)

Use the development package **`ZAD164_EX_###`**, where **`###`** is your personal suffix (_group ID_), to complete the exercises of this hands-on workshop.

Due to time constraints, we've already generated the exercise packages and the database tables for storing travel data (`ZAD164_EVLOG_###`), booking data (`ZAD164_BOOK_###`), and event data (`ZAD164_EVLOG_###`). These development objects provide the starting points of the exercises. 

Travel and booking demo data can be filled in the relevant tables by executing (**F9**) the class ![ ](../images/adt_class.png)**`ZCL_AD164_FILL_TABLES_###`**. 

> [!NOTE] 
> If you don't have access to a prepared ABAP system provided by SAP, you'll need to **create your own exercise package and a few development objects** before starting with the first exercise. Follow the instructions provided below to do so.
> 
> <details>
> <summary>Click to expand!</summary>
>     
> Create the development objects below in your system. 
>  
> Replace all occurrences of the placeholder **`###`** in the provided code snippets with your personal suffix. 
> You can use the ADT function _**Find and Replace**_ (**Ctrl+F**) to do this.
>    
> 1. Create the development package ![ ](../images/adt_package.png)**`ZAD164_EX_###`** with **`ZLOCAL`** as super package ("_ABAP for Cloud development_" as language version). 
> 2. Create the database table ![ ](../images/adt_tabl.png)**`ZAD164_TRVL_###`** – for storing the travel data ([📄source code](images/ex0_tabl_zad164_trvl.txt)).
> 3. Create the database table ![ ](../images/adt_tabl.png)**`ZAD164_BOOK_###`** – for storing the booking data ([📄source code](images/ex0_tabl_zad164_book.txt)).
> 4. Create the database table ![ ](../images/adt_tabl.png)**`ZAD164_EVLOG_###`** – for storing the event data ([📄source code](images/ex0_tabl_zad164_evlog.txt)).
> 5. Create the global class ![ ](../images/adt_class.png)**`ZCL_AD164_FILL_TABLES_###`** – for generating demo travel and booking data ([📄source code](images/ex0_class_zcl_ad164_fill_tables.txt)).

</details>

<!--

## Working with Github
[^Top of page](#)

Here are a few tips to complete this exercise on GitHub.

<details>
  <summary>🔵 Click to expand!</summary>
  
  **Use the outline**  
  🚧

  **Use the _Copy Raw Content_ function**  
  🚧

  **???**  
  🚧

</details>

-->

## Helpful Information
[^Top of page](#)

This section contains some helpful information for the exercises: _Find/Replace_ functionality, modern ABAP syntax, and useful ADT shortcuts.

<details>
  <summary>🔵 Click to expand!</summary>
 
### Find/Replace
In the course of these exercises you will frequently see the task to "_replace the placeholder **`###`** with your assigned suffix_", where *###* is your assigned suffix. 

For this it's recommended to make use of the **Find/Replace** feature of the Eclipse Editor. It can be opened either via the menu (**_Edit -> Find/Replace..._**) or via **Ctrl+F**.
  
 ![find and replace](images/find01.png)
   
Choosing **Replace All** allows you to replace all occurrences of **`###`** with your assigned suffix.


### ABAP Pretty Printer (ABAP Formatter)

You can make use of the shortcut **`Shift + F1`** to format your source code. You may need to configure on first use.

### Modern ABAP Syntax
The modern, declarative, and expression-oriented ABAP language syntax will be used in the different exercises. It allows developers to write more simple and concise source code using new language features like inline declarations, constructor expressions.

> **Find more information in the ABAP Keyword Documentation**: [ABAP - Programming Language](https://help.sap.com/doc/abapdocu_cp_index_htm/CLOUD/en-US/index.htm?file=abenabap_reference.htm) 
  
### Useful ADT Shortcuts
Here are some useful ADT keyboard shortcuts for the ABAP development in Eclipse.

![ADT Shortcuts](images/adt_shortcuts.png)

More useful ADT shortcuts can be found here: [Link](https://blogs.sap.com/2013/11/21/useful-keyboard-shortcuts-for-abap-in-eclipse/).

> **Info**: You can display the full list of available shortcuts in the **Show Key Assit** in ADT by pressing **Ctrl+Shift+L**.
 
</details>

## Summary & Next exercise
[^Top of page](#)

Now you've familiarized yourself with the solutions and your exercise package `ZAD164_EX_###`, where `###` is your personal suffix.

Continue with the next exercise — **[Exercise 1: Define the base BO data model](../ex01/README.md)**.

--
