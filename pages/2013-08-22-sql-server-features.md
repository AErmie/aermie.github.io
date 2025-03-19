---
layout: page
title: SQL Server Features
date: 2013-08-22 21:41
author: AdinErmie
comments: true
categories: []
---
I thought that I would make it easy for everyone and have a page showing the different SQL Server features I install for each System Center product.

As I write the various guides for each specific product, I will update this page to include the SQL Features I use for each of the VMs. That way I can keep the generic guides (i.e. System Center 2012 SP1 in a LAB – Installation Part A to Part D), well, generic.
<h2></h2>
<h2>System Center App Controller (SCAC):</h2>
<ul>
	<li>Database Engine Services</li>
	<li>Management Tools – Basic and Complete (for running queries and configuring SQL services)</li>
</ul>
<h2>System Center Data Protection Manager (SCDPM):</h2>
<ul>
	<li>Database Engine Services</li>
	<li>SQL Server Replication</li>
	<li>Full-Text and Semantic Extractions for Search</li>
	<li>Reporting Services - Native</li>
	<li>Management Tools – Basic and Complete (for running queries and configuring SQL services)</li>
	<li>SQL Client Connectivity SDK</li>
</ul>
<h2><span style="font-style: inherit; line-height: 1.625;">System Center Operations Manager (SCOM):</span></h2>
<ul>
	<li><span style="font-style: inherit; line-height: 1.625;">Database Engine Services</span></li>
	<li><span style="font-style: inherit; line-height: 1.625;">Full-Text and Semantic Extractions for Search</span></li>
	<li><span style="font-style: inherit; line-height: 1.625;">Reporting Services - Native</span></li>
	<li>Analysis Services (see <a title="SCVMM 2012 SP1 in a LAB – Installation Guide (Install Forecasting Analysis Reporting)" href="http://adinermie.com/scvmm-2012-sp1-in-a-lab-installation-guide-install-forecasting-analysis-reporting/" target="_blank">SCVMM Forecasting Analysis Reporting guide</a>)</li>
	<li><span style="font-style: inherit; line-height: 1.625;">Management Tools – Basic and Complete (for running queries and configuring SQL services)</span></li>
</ul>
<h2>System Center Orchestrator (SCORCH):</h2>
<ul>
	<li>Database Engine Services</li>
	<li>Management Tools – Basic and Complete (for running queries and configuring SQL services)</li>
</ul>
<h2>System Center Service Manager (SCSM):</h2>
<h3>SCSM Management Server:</h3>
<ul>
	<li>Database Engine Services</li>
	<li>Full-Text and Semantic Extractions for Search</li>
	<li>Management Tools – Basic and Complete (for running queries and configuring SQL services)</li>
</ul>
<h3> SCSM Warehouse Server:</h3>
<ul>
	<li>Database Engine Services</li>
	<li>Full-Text and Semantic Extractions for Search</li>
	<li>SQL Server Reporting Services (SSRS)
<ul>
	<li>Collation: SQL_Latin1_General_CP1_CI_AS</li>
</ul>
</li>
	<li>SQL Server Analysis Services (SSAS)
<ul>
	<li>Collation: Latin1_General_100_CI_AS</li>
</ul>
</li>
	<li>Management Tools – Basic and Complete (for running queries and configuring SQL services)</li>
</ul>
<h2>System Center Virtual Machine Manager (SCVMM):</h2>
<ul>
	<li><span style="font-style: inherit; line-height: 1.625;">Database Engine Services</span></li>
	<li><span style="font-style: inherit; line-height: 1.625;">Management Tools – Basic and Complete (for running queries and configuring SQL services)</span></li>
</ul>
