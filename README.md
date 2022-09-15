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
  - Create ABAP Project and make the project connected to your backend system 
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


