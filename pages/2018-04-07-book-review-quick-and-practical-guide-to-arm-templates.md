---
layout: page
title: Book Review: Quick and Practical Guide to ARM Templates
date: 2018-04-07 20:34
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2018/03/QuickAndPracticalGuideToARMTemplates_BookCover.jpg"><img class="alignleft size-medium wp-image-30937" src="/wp-content/uploads/2018/03/QuickAndPracticalGuideToARMTemplates_BookCover-188x300.jpg" alt="" width="188" height="300" /></a>Recently, I finished reading the <a href="https://www.amazon.com/dp/B07C8LSBSN" target="_blank" rel="noopener">Quick and Practical Guide to ARM Templates</a> eBook by fellow MVP <a href="https://www.linkedin.com/in/20aman/" target="_blank" rel="noopener">Aman Sharma</a>.

<span style="color: #000000;">Although I am already experienced in creating and using Azure Resource Manager (ARM) templates, I found this book useful in the following ways.</span>
<ul>
 	<li>The Author provides many code examples to assist in understanding the concepts clearly</li>
 	<li>Not a lot of "theory", more practical focus</li>
</ul>
You will notice that the number of highlights and notes may not be very long. This is because I am already familiar with a lot of the concepts and details presented in this book. However, I tried to highlight key points that are of value to someone just starting out into the world of ARM templates.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).

As mentioned in the introduction to this publication...
<ul>
 	<li>ARM Templates can be used for the deployment of resources on both Azure and Azure Stack.</li>
 	<li>ARM templates are Declarative Deployments – All you need to do is declare what you need to deploy. You don't need to create any complex rules or write lengthy scripts.</li>
</ul>
&nbsp;
<h2>Chapter 01: JSON 101 For IT Administrators</h2>
<ul>
 	<li>You can only use double quotes for Properties as they will always be of type string</li>
 	<li>You will have double quotes around Values if they are of string type. You will not have any quotes in case of a number or a boolean value.</li>
 	<li>In JSON the square brackets represent an Array.</li>
</ul>
&nbsp;
<h2>Chapter 02: What Is An ARM Template</h2>
<ul>
 	<li>Parameter Best Practices:
<ul>
 	<li>Try to always provide Default Values</li>
 	<li>Provide metadata so that you can provide insight as to what the parameter is meant for</li>
 	<li>Provide complete descriptive names, no matter how long.</li>
 	<li>Use Pascal Casing to name your parameters. i.e. the First letter should be a small letter. Then every new word will have the first letter as a capital. No space between words. E.g. windowsOSVersion</li>
 	<li>Use properties like minLength and Allowed values to impose restrictions. This reduces any human errors.</li>
</ul>
</li>
 	<li>You use the square parenthesis to indicate to the ARM engine to evaluate whatever is inside the parenthesis. You use the "variable" keyword and then you pass the name of the variable as input.</li>
 	<li>Variable Best Practices:
<ul>
 	<li>Provide complete descriptive names, no matter how long.</li>
 	<li>Use Pascal Casing to name your parameters. i.e. the First letter should be a small letter. Then every new word will have the first letter as a capital. No space between words. E.g. storageAccountName</li>
 	<li>Use the constructs explained in the previous section to dynamically generate variables. This reduces any human errors.</li>
 	<li>Anything that is used more than once and is not required to be entered by an end user, should be created as a variable. Later on, this helps by minimizing the number of places you need to change the value.</li>
</ul>
</li>
 	<li>The dependencies between resources are evaluated and resources are deployed in their dependent order. When resources are not dependent on each other, they are attempted to be deployed in parallel.</li>
</ul>
&nbsp;
<h2>Chapter 03: Helper Functions</h2>
<ul>
 	<li>You use this (the Resource ID) function to determine the ID of a resource. This is only used when the resource (whose ID is needed) is not being deployed in the current template and it already exists in Azure.</li>
 	<li>These are the most common Helper functions that you will use in 80%-90% of the templates. To check the complete list of Helper Functions, check this official link: <a href="https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-template-functions#resource-functions" target="_blank" rel="noopener">Azure Resource Manager template functions</a></li>
</ul>
&nbsp;
<h2>Chapter 04: Building Your First ARM Template</h2>
<ul>
 	<li>As a best practice, provide the metadata, describing what each parameter is for.</li>
 	<li>You should have more tags in case of a production-ready template</li>
</ul>
&nbsp;
<h2>Chapter 05: Deploying Templates Using The Azure Portal</h2>
<ul>
 	<li>None (due to already having experience with this)</li>
</ul>
&nbsp;
<h2>Chapter 06: Deploying Templates Using Azure PowerShell</h2>
<ul>
 	<li>Before deploying the Resource Template to Azure, you should Test it. This step is optional but highly recommended. Use the below cmdlet to test and validate your template: <span style="color: #3366ff;"><em>Test-AzureRmResourceGroupDeployment -ResourceGroupName TestResourceGroup01 -TemplateFile </em></span></li>
 	<li>Key Gotchas
<ul>
 	<li>1. If you provide values for a parameter in both the local parameter file and inline, the inline value takes precedence.</li>
 	<li>2. You cannot use inline parameters with an external parameter file. All inline parameters are ignored when you specify "TemplateParameterUri" parameter.</li>
 	<li>3. As a best practice, do not store sensitive information in the parameters file e.g. Local admin password. Instead of this, either provide these dynamically using inline parameters or store them using the Azure Key vault and then reference the key vault in your parameters file.</li>
</ul>
</li>
</ul>
&nbsp;
<h2>Chapter 07: Creating Parameters File For An ARM Template</h2>
<ul>
 	<li>The parameter names should match to the parameters defined in the ARM template.</li>
</ul>
&nbsp;
<h2>Chapter 08: Authoring ARM Templates Using Visual Studio</h2>
<ul>
 	<li>Notice the JSON Outline panel to the left. This is your biggest friend in Visual Studio when authoring ARM Templates.</li>
</ul>
&nbsp;
<h2>Chapter 09: Deploying ARM Templates Using Visual Studio</h2>
<ul>
 	<li>Note the following points in the parameters:
<ul>
 	<li>a. Corresponding to the string parameters, a text box is provided.</li>
 	<li>b. For the secure string parameters like password, a secure password text box is provided.</li>
 	<li>c. Corresponding to the parameters for which you have defined the "Allowed Values" in your template, a combo box (or drop Down) is provided with the "default Value" selected by default.</li>
</ul>
</li>
</ul>
&nbsp;
<h2>Chapter 10: Iterating And Creating Multiple Instances Of A Resource</h2>
<ul>
 	<li>Note: Arrays are always zero indexed. What that means is that the first element of the array is indexed at 0, the second element of the array is indexed at 1, and so on.</li>
 	<li>Limitations: There are two limitations on the use of the copy to iterate and create multiple resource instances:
<ul>
 	<li>1. Nested Resources - You cannot use a copy loop for a nested resource. If you need to create multiple instances of a resource that you typically define as nested within another resource, you must instead create the resource as a top-level resource and define the relationship with the parent resource through the type and name properties.</li>
 	<li>2. Looping Properties of a Resource - You can only use copy on resource types, not on properties within a resource type. E.g. Creating multiple data disks within a VM.</li>
</ul>
</li>
</ul>
&nbsp;
<h2>Chapter 11: Visualizing ARM Templates And Generating Diagrams</h2>
<ul>
 	<li>Microsoft has provided an Open Source tool for this named "ARMVIZ" (short for ARM Visualizer). This tool can be accessed by navigating to the below URL: <a href="http://armviz.io/" target="_blank" rel="noopener">http://armviz.io/</a></li>
 	<li>Note: If there will be mistakes, such as missing parenthesis in your template, the designer will not show any diagram.</li>
 	<li>In conclusion, ARMVIZ can enable you to easily visualize your ARM Templates. It can empower you to generate diagrams for your documentation and to present to your team.</li>
</ul>
&nbsp;
<h2>Chapter 12: Using KeyVault To Securely Provide Information In ARM Templates</h2>
<ul>
 	<li>Set the Advanced Access Policies to indicate that this key vault can be accessed via ARM Templates.</li>
</ul>
&nbsp;
<h2>Chapter 13: Providing PowerShell Scripts To Run After VM Deployment Via ARM Templates</h2>
<ul>
 	<li>You first need to have PowerShell script files uploaded to a storage account. To do this you add an Extension resource(Microsoft.Compute/virtualMachines/extensions) nested inside a VM. This extension resource should be of type "CustomScriptExtension". You provide the URLs to the PowerShell scripts inside this custom script extension.</li>
 	<li>If there are more than one scripts then there should be one master script amongst all ps1 files which will internally invoke other files. This master file will be triggered via the template. Information of all file URLs will also be provided via the Template</li>
 	<li>How it works:
<ul>
 	<li>Both the files i.e. start.ps1 and secondaryScript.ps1 are picked up from the storage account after VM deployment. Ensure to replace the URLs with your actual storage account blob URLs. You can add more files if needed.</li>
 	<li>The "start.ps1" is the main PowerShell script which should be invoking the secondaryScript.ps1 internally</li>
 	<li>CommandToExecutre property is used to invoke the start.ps1 PowerShell script on the deployed VM</li>
</ul>
</li>
</ul>
&nbsp;
<h2>Chapter 14: Deploying A Windows VM With OMS Integration Via ARM Templates</h2>
<ul>
 	<li>You can also provide the Workspace Id and the Workspace Key dynamically by only using the OMS Workspace name.</li>
 	<li>Reference: You can check the complete quick starter template for OMS integration here: <a href="https://github.com/Azure/azure-quickstart-templates/tree/master/201-oms-extension-windows-vm" target="_blank" rel="noopener">GitHub Sample - Deployment of a Windows VM with OMS Extension</a></li>
</ul>
&nbsp;
<h2>Chapter 15: Creating ARM Templates From An Existing Azure Infrastructure And Modifying It</h2>
<ul>
 	<li>This Power Tip is really easy if you know just the option.
<ul>
 	<li>1. If you want to make the template for all the resources in a Resource Group in Azure, then go to the properties of the Resource Group and find the option for "Automation Script".</li>
 	<li>2. If you want to get the template only for a particular resource, then navigate to that resource in the Azure Portal and then open its settings. You will find the same "Automation Script" option.</li>
</ul>
</li>
 	<li>After downloading, you should start cleaning up the template. There are only 4 major tasks that you need to perform as part of the cleanup:
<ul>
 	<li>1. Remove any hard-coded values for various dependent resources e.g. NIC for a VM, VHD for a VM etc.</li>
 	<li>2. Remove any resources and dependent parameters that you don't need.</li>
 	<li>3. Create Parameters for the values you want to change for each deployment and want the end user to provide during the deployment.</li>
 	<li>4. Create Variables for the values which can have fixed values but are being used at multiple locations in your template.</li>
</ul>
</li>
</ul>
&nbsp;
