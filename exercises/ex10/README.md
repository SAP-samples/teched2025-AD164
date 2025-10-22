# \[Optional\] Exercise 10: Working with the Entity Manipulation Language (EML)

In the previous exercise, you've enhanced the Travel BO to support full transactional behavior – that is full create, update, and delete operations, and enable draft handling to temporarily store transient data until it is persisted in the database – [Exercise 9](../ex09/README.md). 

In this exercise, you will explore how to use the Entity Manipulation Language (EML) to consume – that is, read, update, create, and delete – instances of the _Travel_ BO via APIs from outside the RAP BO as well as outside of the RAP context. You will create the ABAP class `ZCL_AD164_EML_###` which contains sample access implementations via the EML APIs to the Travel BO is provided for the purpose. 

You will have the opportunity to test the _privileged mode_ enabled in [_Exercise 8_](../ex08/README.md).

**Exercise steps:**

- [Exercise 10.1: Create the ABAP Class](#exercise-101-create-the-abap-class)
- Exercise 10.2: ???
- Exercise 10.3: ???
- Exercise 10.4: ???
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


## Exercise 10.1: Create the ABAP Class

> In this step you will create the class ![class icon](../images/adt_class.png)`ZCL_AD164_EML_###` to explore the Entity Manipulation Language.  

<details>
  <summary>🔵Click to expand!</summary>   
 
1.	Right-click on your package ![package icon](../images/adt_package.png)**`ZAD164_EX_###`** and choose _**New > ABAP Class**_
      
2.	Maintain the needed information (where `###` is your group ID) and choose **Next >** to continue.

     * Name: **`ZCL_AD164_EML_###`**
     * Description: _**`EML Playground`**_
     * Interfaces: **`if_oo_adt_classrun`**   
       For that, press _**Add**_, enter the interface name in the filter area, choose the correct entry from the list, and confirm with **OK**.
        
    Assign a transport request if needed and choose **Finish** to create the class.  
         
    The ABAP class skeleton is generated and displayed in the class editor.  
    
    ![ABAP Class](images/ad164_101_emlclass01.png)
    
3.	Delete the complete ABAP class skeleton in the global class, replace it with the source code provided in the document (🟡📄) below, and replace all occurences of **`###`** with your personal suffix using the _Replace All_ function (**Ctrl+F**).
 
    🟡📄 **Source code document**: ![class icon](../images/adt_class.png)[ABAP Class: ZCL_AD164_EML_###](images/EX10_CLASS_ZCL_AD164_EML.txt)

5.	Save ![save icon](../images/adt_save.png) and activate ![activate icon](../images/adt_activate.png) the class.  
  
</details>


## Exercise 10.2: Play around and get familiar with EML

> After completing these steps you will have....

<details>
  <summary>🔵Click to expand!</summary>   
 
1. blablabla...
2. blablabla...
3. blablabla...

 <details>
   <summary>📄 Click to expand!</summary>
   <pre lang="ABAP">
   </pre>
  
   > **Brief explanation of the local RAP event handler class `lhe_travel`**
   > <details>
   >    <summary>ℹ️ Click to expand the details!</summary>
   >           
   > 
   > </details>    
  
 </details>

2. Save![ ](images/adt_save.png) (**Ctrl+S**) and activate![ ](images/adt_activate.png) (**Ctrl+F3**) the changes.
           
</details> 

<!--

## Exercise 10.3: ...

> After completing these steps you will have....

<details>
  <summary>🔵Click to expand!</summary>   
 
1. blablabla...
2. blablabla...
3. blablabla...

 <details>
   <summary>📄 Click to expand!</summary>
   <pre lang="ABAP">
   </pre>
  
   > **Brief explanation of the local RAP event handler class `lhe_travel`**
   > <details>
   >    <summary>ℹ️ Click to expand the details!</summary>
   >           
   > 
   > </details>    
  
 </details>

2. Save![ ](../images/adt_save.png) (**Ctrl+S**) and activate![ ](../images/adt_activate.png) (**Ctrl+F3**) the changes.
           
</details> 


## Exercise 10.4: Preview and test the enhanced app

> After completing these steps you will have....

<details>
  <summary>🔵Click to expand!</summary>   
 
1. blablabla...
2. blablabla...
3. blablabla...

 <details>
   <summary>📄 Click to expand!</summary>
   <pre lang="ABAP">
   </pre>
  
   > **Brief explanation of the local RAP event handler class `lhe_travel`**
   > <details>
   >    <summary>ℹ️ Click to expand the details!</summary>
   >           
   > 
   > </details>      
 </details>

     
</details> 

-->   


## Summary

Congratulations!🎉 You've now completed the optional exercises of this hands-on workshop as well!

Return to **[Home - AD164](../README.md)**

---
