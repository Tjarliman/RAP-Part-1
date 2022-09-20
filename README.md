# ABAP Restful Programming Model Concept-Part-1

This document intended for internal session to understand the concept and start hands-on into the RAP.
In this part 1, we will see how to implement the concept to build an application.

# Create a list (Header-detail)

First lesson is that we will create an app as a list of data comming from 2 sources table (Header and detail).
Header table name ZTJ_FIDOC, detail table name ZTJ_FIDOCI

# Pre-requisites

- Eclipse installed in your computer
- Have access to the back end system

#Step 1 - Create data model for the header and detail

#Step 1.1 - Create ABAP Project

  - Open Eclipse
  - Create ABAP Project and make sure the project connected to your backend system 
  - ![image](https://user-images.githubusercontent.com/39553318/190315283-8c2d53cd-4cd0-45e4-a317-2106d9a737cf.png)
  - ![image](https://user-images.githubusercontent.com/39553318/190315672-f463e078-cd99-41aa-aaf8-2d6e66127f25.png)
  - Follow the instruction from the wizard, until you create a project in your eclipse
  - ![image](https://user-images.githubusercontent.com/39553318/190315900-4da82a5a-8e49-4f3f-aee5-89db0a1f0fa4.png)

#Step 1.2 - Create Header CDS view

  - inside the created ABAP project, create a CDS view and we are going to put it as a header view, let's put a name Znn_FIDOC where nn is your unique ID (but you cannot use ID which is already used by other participants)
  - get the file ZTJ_I_FIDOC_U.txt, and copy and past the code in that file to your CDS view
  - change this parts in yellow, to your name space, example: ZTJ_xxx -> Znn_xxx
  - ![image](https://user-images.githubusercontent.com/39553318/190317063-e59b686c-10ad-43ed-b5fd-08d85f50f4a0.png)
  - save it, but dont activate it yet since you need to create another CDS view which is the detail CDS view

#Step 1.3 - Create Detail CDS view

  - create another CDS view, and copy and paste the code from file ZTJ_I_FIDOCI.txt to this new CDS view
  - dont forget to change the name of the entity, example: ZTJ_xxx -> Znn_xxx
  - save it, and select the "activate all" button, and select both the header and detail CDS views.
  - ![image](https://user-images.githubusercontent.com/39553318/190332570-189ef939-8bd4-4899-a74f-2b182ae3caa1.png)

#Note: There are other CDS views which you need to have them as well in your system like ZTJ_I_FIDOC_SKA1_VH, ZTJ_I_FIDOC_T001_VH, ZTJ_I_FIDOC_TCURC_VH you can just re-use them.
Once you have activated both the header and detail CDS views, then our next step is to create projection views out of these CDS views.

#Step 2. Create Business Service Provisioning.

In this step, we will create a projection views, metadata extensions, and generate the OData services.

#Step 2.1 Create Header and detail Projection Views

  - create a new CDS view, with type projection view, you can copy and paste the code from the file ZTJ_C_FIDOC_U.txt to create Header Projection view
  - create a new CDS view, with type projection view, you can copy and paste the code from the file ZTJ_C_FIDOCI_U.txt to create Detail Projection view
  - dont forget to change the name of the entity, example: ZTJ_xxx -> Znn_xxx
  - also dont forget to save and activate both CDS views.

#Step 2.2 Create Metadata extention for Header and Detail Project views.

In this step, we will create a metadata extension for each Header and Detail views. This metada extension is actually another type of CDS view. But, as best practise, we will put some annotations into this view, and these annotations are actually to define which fields are going to be put at the selection field parts or line item part, or Facet...etc.

  - Create metadata extension for header projection view. You can copy and paste the code in file ZTJ_C_FIDOC_U_me.txt
  - Create metadata extension for detail projection view. You can copy and paste the code in file ZTJ_C_FIDOCI_U_me.txt
  - dont forget to change the name of the entity, example: ZTJ_xxx -> Znn_xxx
  - also dont forget to save and activate both CDS views.

Once you have activated both the metadata extension views. Then you are ready to expose our projection views as OData service.

#Step 2.3 Create Service Definition

Since in this hands-on, we will only create a list, not a transactional application then we dont need to create any Behaviour Defitions.

  - Create a service definitions, and name it similar to this name (followed our naming convention), ZTJ_UI_C_FIDOC_U.
  - Right click on one the consumption views then select Create Service Definition
  
  ![image](https://user-images.githubusercontent.com/39553318/191144715-eebd57f5-9f0b-4213-a652-06ed50824057.png)

  - dont forget to change the name of the entity, example: ZTJ_xxx -> Znn_xxx
  - and just a code like below
  - ![image](https://user-images.githubusercontent.com/39553318/190342312-74e59b0b-1054-4642-b57c-eff3a122c953.png)
  - save and activate it.

#Step 2.4 Create Service Binding

In this step, we will publish our service definition to allow any apps to connect to / use this service as an OData service.

  - Right click on the Service Definition you created in the previous step
  - Click Create Service Binding
  - You should be able to see this screen
  - ![image](https://user-images.githubusercontent.com/39553318/190343341-d3433d09-1ad9-4f52-929a-78c11d0e302d.png)
  - Once created, you should be able to see another screen like below
  - ![image](https://user-images.githubusercontent.com/39553318/190343616-c908db8f-e415-42f3-bf5e-98d496fbc301.png)
  - Then what you need to do is just clicking the Publish button, once publised you should be able to see something like this 
  - ![image](https://user-images.githubusercontent.com/39553318/190343787-b390a952-a8c1-4a30-af03-61c2035a8080.png)
  - No need to activate it
  
#Step 2.5 Preview the OData Service.

Basically once you have completed until this step. Then you should be able to see how your application would looks like.
From the last screen you saw on the last step, you can select the header entity (ZTJ_C_FIDOC), then click the Preview button
![image](https://user-images.githubusercontent.com/39553318/190344770-bff49963-abbd-45e1-829a-b28e9f85c907.png)
and then your service will be displayed in your default browser as an app.

![image](https://user-images.githubusercontent.com/39553318/191235149-84315a0d-a16b-47b8-a528-bafa95a06b2a.png)

That's it.
Up to now, you did not create any logic/program code related to this app, and actually you dont need to. Because the RAP framework will create the codes for you. (Do you know, which code I am talking about?)

Now you can continue to create an application based on this service by using Business Application Studio (BAS) in SAP BTP, or Visual Studio Code.
During creation of the app, you need to pick / create application which will be based on Fiori Element.
Unfortunately , we will not cover that in this session.


GOOD LUCK !!!

