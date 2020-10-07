
# **OpenShift Virtualization**

# Installing Operator:

Step 1:

Open the Operator HUB in OpenShift web console and search virtualization in search filter. Select the **OpenShift Virtualization** tile and click to install.

![](RackMultipart20201007-4-1f8iwlg_html_f5b4f1ec5525e74f.png)

Step 2:

Select the Operator recommended namespace **openshift-cnv** and choose the version and approval strategy.

Note: While trying to create the namespace through OpenShift CLI. It will not allow to create specified namespace. So choose recommended namespace it will automatically create the namespace at backend.

![](RackMultipart20201007-4-1f8iwlg_html_e1a8fef16dcf814b.png)

Step 3:

Click the Installed Operators and will see the status of the Operator Installation and Click the **CNV Operator Deployment** in Provided APIs tap.

![](RackMultipart20201007-4-1f8iwlg_html_bb980f8beae56566.png)

Step 4:

Create **Create HyperConverged** Cluster with default YAML valuesin **CNV Operator Deployment** page.

![](RackMultipart20201007-4-1f8iwlg_html_b7bf1a18b3cceaf5.png)

Once you created the cluster check the pods are running.

# Creating Virtual machine USING URL

Step 1:

After successful Operator Installation click Virtual Machine in Workloads section.

![](RackMultipart20201007-4-1f8iwlg_html_260b58a0d13f19f7.png)

Step 2:

Create the VM with the following option

- New with Wizard.
- Important with Wizard.
- New From YAML.

Optionally you can also create the VM using Virtual Machine Templates.

## Creating VM with New Wizard

Step 3:

Before creating VM need to create the Disk. Create the PVC where you are going to create the VM( Select namespace ). Create the PVC in OpenShift web console Storage section. Select Storage Class and name of the PVC and Access Mode , Size.

![](RackMultipart20201007-4-1f8iwlg_html_69c4a9df2f0e89f2.png)

Step 4:

Once you created the PVC. Navigate to Workloads-\&gt;Virtual Machine. Click the Create Virtual Machine with &quot;New Wizard&quot;.

![](RackMultipart20201007-4-1f8iwlg_html_c28a0161b9141d8e.png)

Step 5:

Creating Virtual Machine with following sources.

- PXE
- URL
- Container
- Disk

For this case we are going to use URL.

Step 6:

Select the Source as URL and Give the URL of ISO image which you downloaded and uploaded into any S3 Bucket storage. Select OS and Flavour ( SIZE OF THE VM) , Workload Profile ( Server, Desktop etc..), Name of the VM. Finally Click Next button.

![](RackMultipart20201007-4-1f8iwlg_html_861a9bd9715b572b.png)

Step 7:

Networking of the VM. By default we are going POD Networking. So there is no change in the section. Click Next button.

![](RackMultipart20201007-4-1f8iwlg_html_468ba47b528cc76e.png)

Edit the Network Interface and updated network type **bridge**.

![](RackMultipart20201007-4-1f8iwlg_html_f51721ac33e805b6.png)

Step 8:

In the Storage section by default disk displayed with the size of 10 GB and Source is URL. If you want modify the disk clicking of 3 dot in the right side corner. Here this will act as bootable disk. Click add disk button add the new disk with our existing PVC.

![](RackMultipart20201007-4-1f8iwlg_html_e88384a1e144894e.png)

Step 9:

In the additional disk screen select source as **Attach Disk** and **Select your PVC which you created earlier.** Navigate to the next section **Advanced Section .** We are not going to change anything in **Cloud-init** and **Virtual Hardware.**

![](RackMultipart20201007-4-1f8iwlg_html_50d0000045a529f8.png)

**Cloud-init**

![](RackMultipart20201007-4-1f8iwlg_html_4d2d7f969e6f134a.png)

**Virtual Hardware**

Step 10: ![](RackMultipart20201007-4-1f8iwlg_html_1b07074ae2df06dc.png)

Step 10:

Finally review your changes and click the **Create Virtual Machine** button.

![](RackMultipart20201007-4-1f8iwlg_html_368454b130fce5da.png)

Step 11:

Once your OS Installation done. You have to remove your bootable disk in VM Details page.

![](RackMultipart20201007-4-1f8iwlg_html_2ed7d026a05c0b36.png)

**Author: Muthu Sundaravadivel**
