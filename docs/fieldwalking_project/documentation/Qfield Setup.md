---
layout: default
---

# Qfield Setup Documentation

## Introduction

This is a custom fieldwalking Qfield project which I have created for all to use and adapt however you see fit. Each project will have different recording priorities so feel free to mess around with this project as much as you need to. I hope this version gives you an idea of what can be achieved.

Some things to make clear before you begin with this data. The geopackage contains a QGIS project. this walkthrough will guide you through converting that QGIS project into a Qfield project ready to use on whichever mobile device you have access to.

### 1. Downloading the data

First of all you need to download the geopackage from this repository. To do that firstly click onto the geopackage in Github and click Raw (below). Make sure to save the geopackage somewhere sensible!

<img width="867" height="290" alt="image" src="https://github.com/user-attachments/assets/c0a028f3-fb33-4a93-9779-7f71adea1e81" />


Next open up a blank QGIS project and add the geopackage connection in your browser panel.

## 2. Connecting the data to QGIS

### Making sure your browser panel is turned on

If you are struggling with this step, firstly you need to make sure your browser panel is displaying. to check this click on the view dropdown at the top of your window.

<img width="807" height="475" alt="image" src="https://github.com/user-attachments/assets/03514ba2-a36f-4e81-8f73-fb6659eb376c" />

 Navigate to Panels and toggle the Browser option
<img width="781" height="478" alt="image" src="https://github.com/user-attachments/assets/12f0e655-87f7-4f4c-83f4-a6eb3495e578" />

This should ensure that your Browser panel is visible with your GeoPackage option - it is a good idea to leave this panel showing.

<img width="1392" height="678" alt="image" src="https://github.com/user-attachments/assets/c5898f33-42d5-4d18-a78c-9eee035e4be4" />


### Adding the GeoPackage connection

To add the connection to the geopackage, right click on GeoPackage (see above) and then select new connection.
<img width="428" height="390" alt="image" src="https://github.com/user-attachments/assets/399f3a42-0718-401f-b11b-99682a40da39" />

Then simply navigate to where ever you saved the downloaded GeoPackage. NOTE if you add the connection and then move the location of the GeoPackage to a new folder, you will need to re add the connection. It is a good idea to save the original GeoPackage in a folder that will not change to avoid having to re-link your data.

## 3. Opening the project

<img width="395" height="523" alt="image" src="https://github.com/user-attachments/assets/de6716e0-8dce-4874-84a8-486a91f5d0bc" />


Expand the GeoPackage layer and you will see the GIS layers inside and also the QGIS project. Double click on the QGIS logo to open up the Fieldwalking project in QGIS.

Once you have the project open - you are free to edit and add to the data as you wish. I have created layers and symbology to the project how I saw best fit, but your project will be unique and you may have certain bits of information that you want to record that I have not included. Have a play around with it!

# How to get the data into Qfield


## 1. Create a Qfield Account

The first step to getting the project into Qfield and onto your phone ready to begin fieldwalking, is to create a Qfield account by visiting https://app.qfield.cloud/accounts/login/.

## 2. Install the Qfield Plugin inside QGIS

Navigate to the Plugin dropdown at the top of your toolbar and select Manage and Install Plugins...

<img width="870" height="331" alt="image" src="https://github.com/user-attachments/assets/619e0bb5-53c9-4325-85bb-3f91004724bb" />


Search for Qfield Sync and install the plugin

<img width="863" height="732" alt="image" src="https://github.com/user-attachments/assets/9ee80bb8-0cf4-490a-ad59-0f58cdebe8f3" />


You will then notice several new buttons have appeared in your QGIS (below)

<img width="332" height="97" alt="image" src="https://github.com/user-attachments/assets/5bbca6b8-9e17-47de-8b21-20ea40bc2fb5" />


Click on the blue cloud icon and sign in with your Qfield details.

## 3. Converting the project to a Qfield Cloud project

With the project open and logging into your Qfield plugin. Navigate to Create New Project (below). This will create a new project by converting the project you already have open.

<img width="862" height="911" alt="image" src="https://github.com/user-attachments/assets/4b57dd13-e1a0-479f-910f-76a02db1d973" />


Check Convert currently open project and press next.

<img width="861" height="517" alt="image" src="https://github.com/user-attachments/assets/6972afd3-7243-4cc8-8181-98e1125cf32c" />


Then choose a location to save the project folder on your machine.

<img width="863" height="822" alt="image" src="https://github.com/user-attachments/assets/cc98be54-e81c-40f0-99bf-1ca6b0cec830" />


This is the local copy of your Qfield project. Any changes you make to this version of the project will be made in Qfield on your mobile - as long as you push the changes.

Congratulations you now have a fieldwalking project! Log into your Qfield app, navigate to cloud projects and download your project to the phone.
