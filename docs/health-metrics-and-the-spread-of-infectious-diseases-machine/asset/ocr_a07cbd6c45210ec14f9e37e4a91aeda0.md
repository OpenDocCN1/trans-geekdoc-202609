# Spatial Data Modelling and Visualisation

Learning Objectives

+   - Learn how to model and visualise spatial data
- Understand the concepts of spatial data, spatial data models, and spatial models
- Create maps, simulate infections, and predict the spatial distribution of phenomena

In the previous chapters, we explored the fundamentals of data visualisation with various techniques for creating static and interactive plots. In this chapter, we will learn how to model and envisage spatial data, which involves analysing and representing data with spatial components. We will explore the concepts of spatial data, spatial data models, and learn how to create maps, simulate infections, and predict the spatial distribution of phenomena such as disease spread. By combining spatial data with machine learning techniques, we can model the spatial dynamics of disease transmission and assess the risks associated with the spread of infections. We will use various packages such as sf, ggplot2, and gstat to create spatial models and visualisations, and gain insights into the spatial distribution of infections in a specific region.

# 12.1 Spatial Data, Spatial Data Models, and Spatial Models

Understanding the spatial distribution of phenomena such as disease spread, land cover changes, or climate patterns requires the use of spatial data and spatial models. These tools are essential for analysing and predicting spatial processes and for informing data-driven decisions in public health, environmental management, and urban planning.

A notable example is the Ebola Virus outbreak in West Africa (2014–2016). The virus spread across countries like Guinea, Liberia, and Sierra Leone, driven by factors such as population density, healthcare infrastructure, and human mobility. By analysing spatial data on cases, fatalities, and healthcare facilities and applying spatial models to simulate the virus's spread, researchers gained valuable insights into the dynamics of the outbreak. This analysis helped identify high-risk areas for targeted interventions.¹1

+   - **Spatial Data:** This refers to data that includes geographic coordinates, addresses, or boundaries, representing the physical location of objects or events. Spatial data can be stored in two formats: vector and raster. Vector data use geometric shapes

> ¹Null, "Ebola Virus Disease in West Africa — the First 9 Months of the Epidemic and Forward Projections," New England Journal of Medicine 371, no. 16 (October 16, 2014): 1481-95, doi:10.1056/NEJMoa1411100.