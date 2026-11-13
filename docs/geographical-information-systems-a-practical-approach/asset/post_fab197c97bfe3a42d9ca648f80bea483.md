
## GEOGRAPHICAL INFORMATION SYSTEMS
### SECOND EDITION
### A Practical Approach
### Xuan Zhu
### ROUTLEDGE

## Geographical Information Systems

Geographical information systems (GIS) are powerful tools for reporting on the environment, natural resources and social and economic development; modelling the environmental, biophysical, social and economic processes; assessing environmental and social impacts; evaluating environmental, social and economic policies and actions and disseminating spatial information. _Geographical Information Systems: A Practical Approach_ provides the fullest available introduction to GIS and their environmental, social and economic applications. This new edition has been substantially revised and updated to incorporate the key developments in GIS technology and spatial data science and their applications that have taken place in recent years.
The key features include:

- A comprehensive coverage of concepts, methods, techniques and tools in GIS for spatial data capturing, processing, visualisation, analysis, modelling and decision-making.
- Incorporation of advanced machine learning techniques for spatial data analysis and modelling.
- Extended coverage of spatial visualisation with 3D mapping and online mapping.
- Weaving together of GIS theory and practice to help readers learn important GIS concepts and methods and develop their understanding through practicals with ArcGIS Pro or QGIS.
- New and updated case studies illustrating the innovative use of GIS for a wide range of applications.

The second edition of this text continues to bring up-to-date GIS knowledge, tools and practices into one cohesive, comprehensive, concise and self-contained book which is accessible to students, scientists and practitioners in environmental science, earth science, geography, archaeology and other scientific studies that have a spatial dimension.

**Xuan Zhu** is Senior Lecturer in the School of Earth, Atmosphere and Environment, Monash University, Australia. He received his PhD from the University of Edinburgh and has over 30 years of international experience in GIS and remote sensing and their applications in environmental and regional resource use planning. Dr Zhu is the author/co-author/co-editor of four academic books and over 100 academic papers and book chapters.

Taylor & Francis
Taylor & Francis Group
http://taylorandfrancis.com

## Geographical Information Systems
### A Practical Approach
### Second Edition
### Xuan Zhu

Designed cover image: Chris Gordon / Getty Images

Second edition published 2025
by Routledge
4 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN

and by Routledge
605 Third Avenue, New York, NY 10158

Routledge is an imprint of the Taylor & Francis Group, an informa business

© 2025 Xuan Zhu

The right of Xuan Zhu to be identified as author of this work has been asserted in accordance with sections 77 and 78 of the Copyright, Designs and Patents Act 1988.

All rights reserved. No part of this book may be reprinted or reproduced or utilised in any form or by any electronic, mechanical, or other means, now known or hereafter invented, including photocopying and recording, or in any information storage or retrieval system, without permission in writing from the publishers.

Trademark notice: Product or corporate names may be trademarks or registered trademarks, and are used only for identification and explanation without intent to infringe.

First edition published by Routledge 2016

## British Library Cataloguing-in-Publication Data

A catalogue record for this book is available from the British Library

ISBN: 9781032380445 (hbk)
ISBN: 9781032380469 (pbk)
ISBN: 9781003343226 (ebk)

DOI: 10.4324/9781003343226

Typeset in Adobe Caslon
by Apex CoVantage, LLC

Access the Support Material: https://routledgetextbooks.com/textbooks/instructor_downloads/

In memory of my father, Baiming Zhu (1925–2009), and my mother, Shuzhen Li (1928–2022).

Taylor & Francis
Taylor & Francis Group
http://taylorandfrancis.com

## Contents

- List of Figures xiii
- List of Tables xxii
- Preface xxiii

- 1 GIS Overview 1
- 1.1 Introduction to GIS 1
- 1.1.1 What Is GIS? 3
- 1.1.2 Components of GIS 6
- 1.2 GIS in a Historical Perspective 15
- 1.3 Roles of GIS in Research, Management and Planning 27
- 1.3.1 Inventory and Monitoring 28
- 1.3.2 Analysis and Modelling 28
- 1.3.3 Visualisation and Communication 30
- 1.4 A General Framework for Problem-Solving with GIS 30
- 1.4.1 Defining the Problem 32
- 1.4.2 Structuring the Problem 33
- 1.4.3 Acquiring and Preparing Data 35
- 1.4.4 Designing a Solution Process 36
- 1.4.5 Implementing the Solution Process and Communicating the Results 37
- 1.5 GIS Software 38
- 1.5.1 Categories of GIS Software 38
- 1.5.2 Proprietary GIS Software 39
- 1.5.3 Open-Source GIS Software 43
- 1.6 Summary 45

- 2 Spatial Data and Data Management 52
- 2.1 The Nature of Spatial Data 52
- 2.1.1 Conceptualisation of Geographical Space 54
- 2.1.2 Map Scale and Spatial Resolution 55
- 2.1.3 Generalisation of Geographical Features 58

- 2.2 Georeferencing Systems 61
- 2.2.1 The Shape of the Earth 61
- 2.2.2 Geographical Coordinate Systems 62
- 2.2.3 Projected Coordinate Systems 65
- 2.3 Spatial Data Models 76
- 2.3.1 Vector Data Model 76
- 2.3.2 Raster Data Model 84
- 2.3.3 Object-Oriented Data Model 89
- 2.4 Spatial Database Management 93
- 2.4.1 Relational Databases 93
- 2.4.2 Georelational Databases 94
- 2.4.3 Object-Relational Databases 96
- 2.5 Summary 104

- 3 Spatial Data Input and Manipulation 109
- 3.1 Spatial Data Capture 109
- 3.1.1 Vector Data Capture 110
- 3.1.2 Raster Data Capture 121
- 3.1.3 Crowdsourcing 121
- 3.2 Spatial Data Transfer 123
- 3.3 Spatial Data Transformation 127
- 3.3.1 Conversion between Vector and Raster 128
- 3.3.2 Geometric Transformation 129
- 3.3.3 Edge Matching 135
- 3.3.4 Line Simplification 137
- 3.4 Spatial Data Editing 139
- 3.4.1 Editing Individual Features 140
- 3.4.2 Editing Features with Shared Geometry 141
- 3.4.3 Editing with Topology Rules 143
- 3.4.4 Editing Attribute Data 145
- 3.5 Spatial Data Quality 146
- 3.5.1 Measures of Spatial Data Quality 147
- 3.5.2 Major Sources of Error in Spatial Data 152
- 3.5.3 Metadata Standards 154
- 3.6 Summary 156

- 4 Spatial Visualisation 161
- 4.1 Cartographic Representations 161
- 4.1.1 Cartographic Elements 162
- 4.1.2 Map Types 163
- 4.2 Map Design 169
- 4.2.1 Selection 169
- 4.2.2 Classification 170
- 4.2.3 Symbolisation 173
- 4.2.4 Layout Design 181
- 4.3 Multivariate Mapping 183
- 4.4 3D Mapping 184
- 4.5 Animated Mapping 199
- 4.5.1 Temporal Cartographic Animations 201
- 4.5.2 Non-Temporal Cartographic Animations 203
- 4.6 Online Mapping 204
- 4.6.1 Technical Components of Online Mapping 208
- 4.6.2 Elements of an Online Map 210
- 4.6.3 Design of an Online Map 212
- 4.7 Summary 216

- 5 Spatial Analysis 221
- 5.1 Scope of Spatial Analysis and Modelling 221
- 5.2 Spatial Query and Reclassification 223
- 5.2.1 Spatial Query 223
- 5.2.2 Reclassification 227
- 5.3 Geometric and Distance Measurement 227
- 5.3.1 Geometric Measurement 228
- 5.3.2 Buffering 231
- 5.3.3 Distance Surface 232
- 5.3.4 Least-Cost Path 236
- 5.3.5 Network Distance 237
- 5.4 Overlay Analysis and Map Algebra 239
- 5.4.1 Vector Overlay 239
- 5.4.2 Raster Overlay 247
- 5.4.3 Map Algebra 247

- 5.5 Spatial Interpolation 255
- 5.5.1 IDW 255
- 5.5.2 Natural Neighbour 258
- 5.5.3 Trend Surface 259
- 5.5.4 Spline 260
- 5.5.5 Kriging 262
- 5.5.6 Accuracy Assessment and Sources of Error 267
- 5.6 Summary 269

- 6 Spatial Data Exploration with Statistics 273
- 6.1 Exploratory Spatial Data Analysis 273
- 6.2 Spatial Sampling 274
- 6.2.1 Spatial Sampling Methods 274
- 6.2.2 Sample Size 277
- 6.3 Measures of Spatial Distributions 277
- 6.3.1 Measures of Central Tendency 277
- 6.3.2 Measures of Dispersion 280
- 6.4 Analysis of Spatial Patterns 286
- 6.4.1 Significance Testing of Spatial Patterns 290
- 6.4.2 Nearest Neighbour Analysis 293
- 6.4.3 Global Moran’s I 295
- 6.5 Detection of Spatial Clusters 298
- 6.5.1 Local Moran’s I 298
- 6.5.2 Getis-Ord G_i* (Hotspot Analysis) 300
- 6.6 Modelling of Spatial Relationships 301
- 6.6.1 Simple Regression 302
- 6.6.2 Multiple Regression 305
- 6.6.3 Geographically Weighted Regression 307
- 6.7 Space-Time Analysis 309
- 6.7.1 Space-Time Data 309
- 6.7.2 Space-Time Cubes 314
- 6.7.3 Space-Time Analysis Methods 317
- 6.8 Summary 329

- 7 Remote Sensing Data Analysis 335
- 7.1 Nature of Remote Sensing Data 335
- 7.1.1 Characteristics of Electromagnetic Radiation 336
