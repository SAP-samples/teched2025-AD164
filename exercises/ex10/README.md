# \[Optional\] Exercise 10: Working with the Entity Manipulation Language (EML)

> [!NOTE] 
> **This exercise is optional.**

## Introduction

In the previous exercise, you've enhanced the Travel BO to support full transactional behavior – that is full create, update, and delete operations, and enable draft handling to temporarily store transient data until it is persisted in the database – [Exercise 9](../ex09/README.md). 

In this exercise, you will explore how to use the Entity Manipulation Language (EML) to consume – that is, read, update, create, and delete – instances of the _Travel_ BO via APIs from outside the RAP BO as well as outside of the RAP context. You will create the ABAP class `ZCL_AD164_EML_###` which contains sample access implementations via the EML APIs to the Travel BO is provided for the purpose. 

You will have the opportunity to test the _privileged mode_ enabled in [_Exercise 8_](../ex08/README.md).

**Exercise steps:**

- [Exercise 10.1: Create the EML playground class](#exercise-101-create-the-abap-class)
- [Exercise 10.2: Play around and get familiar with EML](#exercise-102-play-around-and-get-familiar-with-eml)
- [Summary](#summary)

> [!TIP]
> - Always replace all occurrences of the placeholder **`###`** in the provided code snippets with your personal suffix.
> - Use the ADT function _**Find and Replace All**_ (**Ctrl+F**) to quickly replace text in the source code.
> - Use the ADT function _**Quick Fix**_ (**Ctrl+1**), aka _Quick Assist_, on an erroneous element to get help with resolving the issue.
> - Use the **Show ABAP element info** view (**F2**) to inspect an element in ADT editors.
> - [Useful Keyboard Shortcuts for ABAP Development](https://help.sap.com/docs/ABAP_PLATFORM_NEW/c238d694b825421f940829321ffa326a/4ec299d16e391014adc9fffe4e204223.html?version=latest) (ADT shortcuts)

**ℹ️ About the Entity Manipulation Language (EML)**
<details>
  <summary>Click to expand!</summary>

> The Entity Manipulation Language (EML) is an extension of the ABAP language which offers a type-safe, API-based access to RAP business objects directly by using ABAP. EML has an SQL-like syntax. 
> 
> EML is used to implement the transactional behavior of RAP BOs and also access existing RAP BOs from outside the RAP context.  
> EML interacts with business objects by triggering their operations for specified entities. An operation can only be triggered by EML if the operation is specified for the relevant entity in the behavior definition and if it implemented accordingly.
> 
> When consuming a RAP BO instance via EML, the consumer application is responsible for triggering the `COMMIT` operation after `MODIFY` statement to persist the changes temporary stored in the transactional buffer to the SAP HANA database.
> 
> The EML reference documentation is provided in the ABAP Keyword Documentation. You can use the classic **F1 Help** to get detailed information on each statement by pressing **F1** in the ABAP editors. 
>
> **Further reading**: [EML@RAP Development Guide](https://help.sap.com/docs/btp/sap-abap-restful-application-programming-model/entity-manipulation-language-eml?version=Cloud) | [EML@ABAP Keyword Documentation](https://help.sap.com/doc/abapdocu_cp_index_htm/CLOUD/en-US/abeneml.html)

</details>


## Exercise 10.1: Create the EML playground class

> In this step you will create the class ![class icon](../images/adt_class.png)`ZCL_AD164_EML_###` to explore the Entity Manipulation Language (EML).  

<details>
  <summary>🔵Click to expand!</summary>   
 
1. Right-click on your package ![package icon](../images/adt_package.png)**`ZAD164_EX_###`** and choose _**New > ABAP Class**_
      
2. Maintain the needed information (where `###` is your group ID) and choose **Next >** to continue.

   * Name: **`ZCL_AD164_EML_###`**
   * Description: _**`EML Playground`**_
   * Interfaces: **`if_oo_adt_classrun`**   
       For that, press the _**Add**_ button, enter the interface name in the seach/filter field of the appearing dialog, choose the correct entry  (![package icon](../images/adt_interface.png) `if_oo_adt_classrun`) in the _Matching items_ area, and confirm with **OK**.
        
   Assign a transport request if needed and choose **Finish** to confirm. The ABAP class will be created and the source code skeleton will be displayed in the class editor.  
    
3. Delete the complete source code in the global class, replace it with the source code provided in the document (🟡📄) below, and replace all occurences of **`###`** with your personal suffix using the _Replace All_ function (**Ctrl+F**).

   >> - 💡 Make use of the _Copy Raw Content_ (<img src="../images/copyrawfile.png" alt="" width="3%">) function to copy the source code.
   >> - 🔍 Review the source code and feel free to ask the instructors if anything is unclear.           
     
   🟡📄 **Source code document**: ![class icon](../images/adt_class.png)[ABAP Class: ZCL_AD164_EML_###](images/EX10_CLASS_ZCL_AD164_EML.txt)

5. Save ![save icon](../images/adt_save.png) (**Ctrl+S**) and activate ![activate icon](../images/adt_activate.png) (**Ctrl+F3**) the class.

6. Short explanation of the different methods of the ![ ](../images/adt_class.png)**`ZCL_AD164_EML_###`**

   <img src="images/ad164_10_emlpg01.png" alt="EML Playground" width="40%">
   
   | Method Name | Brief explanation |
   | ------------- |  -- |
   | **`IF_OO_ADT_CLASSRUN~MAIN`** | Main method allowing to run an ABAP class directly in ABAP Development Tools for Eclipse (ADT). |
   | ◈ |   |
   | **`CDS_READ_NONE_PRIVILEGED`** | Method for fetching data via an ABAP SQL _read_ statement on a CDS view **without** _privileged_ mode.  |
   | **`CDS_READ_WITH_PRIVILEGED`** | Method for fetching data via an ABAP SQL _read_ statement on a CDS view **with** _privileged_ mode. |
   | ◈ |   |
   | **`EML_READ_NONE_PRIVILEGED`** | Method for fetching data via an EML _read_ operation **without** _privileged_ mode. |
   | **`EML_READ_WITH_PRIVILEGED`** | Method for fetching data via an EML _read_ operation **with** _privileged_ mode. |
   | ◈ |   |
   | **`EML_MODIFY_NONE_PRIVILEGED`** | Method for data update via an EML _modify_ operation **without** _privileged_ mode. |
   | **`EML_MODIFY_WITH_PRIVILEGED`** | Method for data update via an EML _modify_ operation **with** _privileged_ mode. |
	   
</details>

## Exercise 10.2: Play around and get familiar with EML 

> Play around with the class and get familiar with the EML statements and the _Privileged_ model 

<details>
  <summary>🔵Click to expand!</summary>   
 
1. Press **F9** to run the class in the _**Console**_ view. 
   
   The result of the class run will appear. You can reapeat it.

   💡 You can always use the _clear_ button in _Console_ toolbar to clear it.

   <img src="images/ad164_10_emlpg02.png" alt="EML Playground" width="100%">

   You can re-run (**F9**) the class.

2. You can comment out (**`*`**) some of the method calls in the **`if_oo_adt_classrun~main`** to focus on specific one.

   <img src="images/ad164_10_emlpg03.png" alt="EML Playground" width="70%">

   <br/>
   
   🟠 You may have noticed that the values of the fields **`BookingFee`** and **`TotalPrice`** remain unchanged, event after executing the EML _modify_ methods `EML_MODIFY_NONE_PRIVILEGED` and `EML_MODIFY_WITH_PRIVILEGED`. Let's address this issue in the next step.
    
   <img src="images/ad164_10_emlpg04.png" alt="EML Playground" width="80%">
   
4. To persits authorized data changes resulting von  EML modify statements, a **`COMMIT ENTITIES`** statement must be executed after the statements.
  
   Currently a **`ROLLBACK ENTITIES`** statement is called after the methods **`EML_MODIFY_NONE_PRIVILEGED`** and **`EML_MODIFY_WITH_PRIVILEGED`**.

   Do the following changes: comment out the statement **`ROLLBACK ENTITIES.`** and comment in **`COMMIT ENTITIES.`** in the cource code.

   <img src="images/ad164_10_emlpg05.png" alt="EML Playground" width="40%">
  
5. Save ![save icon](../images/adt_save.png) (**Ctrl+S**) and activate ![activate icon](../images/adt_activate.png) (**Ctrl+F3**) the class.

6. Execute (**F9**) the class at least two times and check the results in the _**Console**_ view. 
   
   The result of the class run will appear. The EML _modify_ call with _privileged_ mode has now been executed and the value of the fields **`BookingFee`** and **`TotalPrice`** is now updated.

   <img src="images/ad164_10_emlpg06.png" alt="EML Playground" width="100%">

5. Go ahead and play around with class.
   
   You can reset your changes anytime using the provided source code (🟡📄).
   
   🟡📄 **Source code document**: ![class icon](../images/adt_class.png)[ABAP Class: ZCL_AD164_EML_###](images/EX10_CLASS_ZCL_AD164_EML.txt)
           
</details> 

## Summary

Congratulations!🎉 You've now completed the optional exercises of this hands-on workshop as well!

Return to **[Home - AD164](../README.md)**

---
