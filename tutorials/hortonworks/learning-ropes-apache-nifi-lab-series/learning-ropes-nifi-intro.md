# NiFi Learning the Ropes Lab Series

Version 1 for HDP 2.4 updated June 13, 2016

## Introduction

Capturing live data is one of the principal challenges facing any organization.  Hortonworks DataFow(HDF) provides an easy to use, graphical, way of handling incoming information.  In addition to its usability, HDF has integrated security(ssl & encryption), scalability(true clustering), and extensible(open source) due to its modular open source architecture.  Businesses have been leveraging this to integrate everything from firewall logs, to manufacturing data, to even real time traffic information.

A city planning board is evaluating the need for a new highway.  This decision is highly dependant on current traffic patterns, particularly as other roadwork initiatives are under way.  Integrating live data poses a problem because traffic Analysis has traditionally been done using historical aggregated traffic counts.  In order to improve the traffic analysis, the city planner wants to also leverage real time data to get a deeper understanding of traffic patterns.  In order to ensure ongoing flexibility, HDF was selected for its many integration points and low barrier to entry.

**Solution Roadmap:**.

1\. Connect to Stream Simulator Traffic Data

2\. Add Geographic Location Enrichment to Data

<!-- Compute and Extract Average speed for 2 transits -->
<!-- Visualize Data with Solr and Banana -->

3\. Ingest Live Stream of Transit Locations

Apache NiFi, one of the technologies that powers HDF, automates the flow of data between systems. The significance of dataflow is to automate and manage the flow of information between systems. This problem space has been around ever since enterprises had more than one system, where some of the systems created data and some of the systems consumed data.

NiFi DataFlow Terms to be familiar with for this Lab Series:

**FlowFile**: The "user data" brought into NiFi is referred to as FlowFile. Attributes(Features & Meta Data) and Content make up the FlowFile.

**Processor**: A predefined set of actions that can manipulate the FlowFiles.  Common processors create, send, receive, transform, route, split, merge and process the data. It is an essential component to build dataflows.

**Connection**: Connects processors in different ways depending on the processing outcome. Each connection contains a FlowFile queue.

**Funnel**: Combines the data from several connections into a single connection.

**Template**: A prebuilt collection of processors & connections that can be used and reused to create a larger dataflow.

**Process Group**: Groups processors together to organize the dataflow in a way, which creates mini dataflows to make one enormous dataflow and makes it easy to understand.

## Pre-Requisites
- Downloaded and Installed Hortonworks Sandbox (Needed for Step 2 if you go with Option 1 for NiFi installation)
- For windows users, to run linux terminal commands in these tutorials, download [Git Bash](https://openhatch.org/missions/windows-setup/install-git-bash).

## Goals and Objectives

Provide an opportunity to interact with components and features of Apache NiFi while building data flow applications. While the underlying flow-based programming is accessible, this lab requires no direct programming and will not dwell on syntax and other features of flow-based programming.

The learning objectives of this lab are to:
- Understand the fundamental concepts of Apache NiFi
- Introduce NiFi’s HTML interface: navigate the UI; design, control, transform and monitor dataflow
- Introduce NiFi processor configuration, relationships, data provenance and documentation
- Create Agile dataflows
- Incorporate API's into NiFi DataFlow
- Learn about NiFi Templates
- Create Process Groups

## Lab Series Overview

In this tutorial, we will learn to build a dataflow that ingests, filters, extracts, enriches and stores moving data. The lab series is based on transit location data gathered from NextBus XML Live Feed. In our lab, we will work with San Francisco Muni Transit agency data: handling vehicle locations, speeds and other variables.

The lab consists of four sections:

**Lab 0** - Learn about your lab environment. Get NiFi up and running on Hortonworks Sandbox or your local machine.

**Lab 1** - Become familiar with NiFi HTML interface. Open NiFi interface; explore its features. Create an agile dataflow project by creating and configuring eleven processors. You will learn to ingest data from transit location xml simulator, extract transit location detail attributes from flowfiles, route those desired attributes to a converted JSON file. Run the dataflow and verify the results in a terminal.

**Lab 2** - Add geographic location enrichment to the dataflow; incorporate Google Places Nearby API into the dataflow to retrieve places nearby the vehicle's location(latitude and longitude). Learn how easy external API integration is with NiFi.

**Lab 3** - Ingest NextBus's live stream data for San Francisco Muni agency.

![Completed-dataflow-for-lab3](/assets/learning-ropes-nifi-lab-series/lab-intro-nifi-learning-ropes/completed-dataflow-rd1-lab3.png)

The dataflow in the image above is what you will learn to build in lab 3. In the introduction of each lab, you are provided a template file of the completed dataflow built for that lab section. The labs are also step by step in which you can build the dataflows from scratch, so we highly encourage the templates be used for verification. Each lab builds on the previous. Feel free to experiment in any way you like, if you get stuck, you can still go onto the next lab with everything in place by selecting the appropriate template.


> Note: **Word about lab instructions**: each section in this guide begins with a description of what you will learn or accomplish in your NiFi training. The essence of these sections is to give you background of what you will do in the lab section. The labs will always be followed by step-by-step instructions.
