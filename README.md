
# **OpenShift Virtualization**

## Openshift  Virtualization Conceptual View

<img src="images/cview.png" width="900" >

## Openshift  Virtualization Architecture Deep Dive View


<img src="images/architectureview.png" width="900" >

## Openshift  Virtualization Operator  View


<img src="images/operatorview.png" width="900" >


# Installing Operator:



***Step 1:***

Open the Operator HUB in OpenShift web console and search virtualization in search filter. Select the **OpenShift Virtualization** tile and click to install.

<img src="images/opertor-hub.png" width="900" >


***Step 2:***

Select the Operator and recommended namespace **openshift-cnv** and choose the version and approval strategy.

***Note:*** While trying to create the namespace through OpenShift CLI. It will not allow to create specified namespace. So recommended namespace automatically create the at the backend process.


<img src="images/opertor-installation.png" width="900" >

***Step 3:***

Click the Installed Operators and will see the status of the Operator Installation and Click the **CNV Operator Deployment** in **Provided APIs** tap.

<img src="images/cnvoperator.png" width="900" >

***Step 4:***

Create **Create HyperConverged** Cluster with default YAML values in **CNV Operator Deployment** page.

<img src="images/hyperconvergedcluster.png" width="900" >

Once you created the cluster check the pods are running.

# Creating Virtual machine Using URL

***Step 1:***

After successful Operator Installation click Virtual Machine in Workloads section.

<img src="images/vm.png" width="900" >

***Step 2:***

Create the VM with the following option

- New with Wizard.
- Important with Wizard.
- New From YAML.

Optionally you can also create the VM using Virtual Machine Templates.

## Creating VM with New Wizard

***Step 3:***

Before creating VM need to create the Disk. Create the PVC where you are going to create the VM( Select namespace ). Create the PVC in OpenShift web console Storage section. Select Storage Class and name of the PVC and Access Mode , Size.

<img src="images/pvc.png" width="900" >

***Step 4:***

Once you created the PVC. Navigate to Workloads and Select the Virtual Machine. Click the Create Virtual Machine with &quot;New Wizard&quot;.

<img src="images/vmdetails.png" width="900" >

***Step 5:***

Creating Virtual Machine with following sources.

- PXE
- URL
- Container
- Disk

For this case we are going to use URL.

***Step 6:***

Select the Source as URL and Give the URL of ISO image which you downloaded and uploaded into any S3 Bucket storage. Select OS and Flavour ( SIZE OF THE VM) , Workload Profile ( Server, Desktop etc..), Name of the VM. Finally Click Next button.

<img src="images/vmdetails1.png" width="900" >

***Step 7:***

Networking of the VM. By default we are going POD Networking.

<img src="images/networkinterface.png" width="900" >

Edit the Network Interface and updated network type **bridge**.

<img src="images/networkinterface1.png" width="900" >

***Step 8:***

In the Storage section by default root disk displayed with the size of 10 GB and Source is URL. If you want modify the disk clicking of 3 dot in the right side corner. Here this will be act as bootable disk. Click add disk button add the new disk with our existing PVC.

<img src="images/additionaldisk.png" width="900" >

***Step 9:***

In the additional disk screen select source as **Attach Disk** and **Select your PVC which you created earlier.** Navigate to the next section **Advanced Section .** We are not going to change anything in **Cloud-init** and **Virtual Hardware.**

<img src="images/additionaldisk1.png" width="900" >

**Cloud-init**

if SSH based authentication needed configure the **SSH Key** otherwise Skip the section.

<img src="images/cloudinit.png" width="900" >

**Virtual Hardware**

If **CD-ROM**  disk needed attach the disk otherwise skip this section. 

<img src="images/virtualhw.png" width="900" >

***Step 10:***

Finally review your configuration changes and click the **Create Virtual Machine** button.

<img src="images/review.png" width="900" >

***Step 11:***

Once the VM created successfully,View VM details. if you have choosen option start VM while creation. it will automatically start, Once the VM creation done. Otherwise you have to manually start the VM.

<img src="images/success.png" width="900" >

***Step 12:***

In the VM details page click the **Console** tap and by default ***VNC Console*** got selected. You can able see OS boot configuration progress.

## OS Installation and Configuration

Based on your ISO image of Operating System the configuration will begins.  For this case, we are using **RHEL 8** ISO image for creating RHEL based Linux VM.

***Step 1:***

Select your langueage and click continue.

<img src="images/languageselection.png" width="900" >

***Step 2:***

RHEL Installation summary page will be displayed. Click the **Installation Destination** . 

<img src="images/setuppage.png" width="900" >

Choose the disk for OS installation and click done.

<img src="images/diskselection.png" width="900" >

***Step 3:***

Select the **Network & Host Name** in  Installation summary page. Enable Ethernet and apply hostname or go with default hostname.

<img src="images/network&host.png" width="900" >

***Step 4:***

In the Installation summary page click **Begin Installation** button. Now the installation getting started.

*** Step 5: ***

While installation  in **USER SETTINGS** page creating root password and username.

usersettings.png

<img src="images/usersettings.png" width="900" >

Set the root Password.

<img src="images/rootpwd.png" width="900" >

Create the Username

<img src="images/usercreation.png" width="900" >

*** Step 6: ***

Once your OS Installation done.  The reboot screen will appear don't start the reboot. Stop the VM and Navigate to the VM details page.

<img src="images/reboot.png" width="900" >

*** Step 7: ***

In the VM details page edit the **Boot Order** and remove the root disk and add the disk which created using PVC.

<img src="images/removerootdisk.png" width="900" >


Start the VM.

*** Step 8: ***

Once you started the VM the Final Cobnfiguration page will appear. Select **License Information** and click the agreement.  

<img src="images/finalconfiguration.png" width="900" >

For this case we are installing RHEL based linux OS. So we need to register the  **REDHAT Subscription Manager** . Once registerd successfully Click the **FINISH CONFIGURATION** button.

<img src="images/rhelsubscritionmanager.png" width="900" >

*** Step 9: ***

Now the OS Installation done. Navigate to the console page and login to your RHEL based LINUX VM using your Username and Password.

<img src="images/rhelhome.png" width="900" >

**Author: Muthu Sundaravadivel**
