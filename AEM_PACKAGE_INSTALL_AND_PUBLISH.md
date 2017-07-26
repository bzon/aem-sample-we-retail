# Install AEM Package and Publish Through Maven
This serves as a reference for installing AEM package and publishing it to its corresponding publish port with the use of maven commands starting from the local installation up to publishing it to its corresponding publish port.

## Pre-requisites
Before you start to deploy your AEM packages, make a list and better take note on the following:  
    - Two (2) copies of the AEM quickstart jar file  
    - Two (2) separate directories for each jar file
  
#### Step 1
Create two (2) separate directories for the AEM quickstart jar files.  
  
Start with the first directory. Name it **Author**.  
For example when using a CLI:  
```
cd ~/Documents/
mkdir Author
```
Then create the second directory. Name it **Publish**.  
For example when using a CLI:  
```
cd ~/Documents/
mkdir Publish
```
  
*Note that the **~** symbolizes the home directory, containing the **Documents** directory, which contains both **Author** and **Publish** directories.*  

#### Step 2
Locate and rename each jar file; one for author/admin, the other for publish.  
  
Start with the author/admin quickstart jar file.  
*Note that the **ports will not be the same** for the author/admin and publish*.  
  
You will initially have this file after download, assuming it is in the **~/Downloads/** directory.  
**AEM_6.3_Quickstart.jar**  
  
Using a CLI, copy the file and place it in the **~/Documents/Author/** directory.  
```
cd ~/Downloads/
cp AEM_6.3_Quickstart.jar ~/Documents/Author
cd ~/Documents/Author
```  
Then you can proceed to rename it using this command.  
```
mv AEM_6.3_Quickstart.jar cq5-author-p4502.jar
```  
*Note that the **-p4502** exposes the port to **4502**, thus, making the author/admin page accessible locally through **"localhost:4502"***.  
  
Next will be the publish port, where you can view your AEM project when deployed. The process is the same as the first but you'll have to use the other directory which is the **Publish** directory and a different name for the publish jar.  
```
cd ~/Downloads/
cp AEM_6.3_Quickstart.jar ~/Documents/Publish
cd ~/Documents/Publish
```  
Same as the first, rename the jar file using this command.  
```
mv AEM_6.3_Quickstart.jar cq5-publish-p4503.jar
```  
*Note that the **-p4503** exposes the port to **4502** so you can access the publish page through **"localhost:4502"**. Here you can view your AEM project if it has been already deployed*.  

**Strictly follow the proper naming convention for the jar files to ensure that they will not encounter issues.**

___
## Maven Commands
#### Cleaning Workspace
Ensure that you start your workspace clean by using this command.  
```
mvn clean
```
  
#### Install Package Locally After Cleaning
Make sure to install your AEM package locally before installing it to the AEM instance.  
```
mvn clean install
```

#### Install Package To AEM Instance  
After installing the AEM package locally, you can now install it to the AEM instance using this command.  
```
mvn clean install -PautoInstallPackage
```

#### Install Package to AEM Instance Then Publish
You can install the AEM package to the AEM instance and at the same time publish it to the publish port so you can view the project through this command.
```
mvn clean install -PautoInstallPackagePublish
```