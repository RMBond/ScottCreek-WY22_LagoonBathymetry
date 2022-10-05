WY22 Scott Creek Lagoon Bathymetric Survey
================
05 October, 2022

-   <a href="#introduction" id="toc-introduction">Introduction</a>
-   <a href="#readme-file-purpose" id="toc-readme-file-purpose">Readme File
    Purpose</a>
-   <a href="#workflow-summary" id="toc-workflow-summary">Workflow
    Summary</a>
    -   <a href="#dataset-descriptions" id="toc-dataset-descriptions">Dataset
        Descriptions</a>
-   <a href="#1-fieldwork-notes" id="toc-1-fieldwork-notes">1. Fieldwork
    Notes</a>
-   <a href="#2-opus-correction" id="toc-2-opus-correction">2. OPUS
    Correction</a>

<!-- README.md is generated from README.Rmd. Please edit that file -->

# Introduction

<img align="Right" width="300" height="300" src="Figures/CZU_perim_SCWatershed_crop_20210426.jpg">

In August 2020, the CZU Lightning Complex fire burned more than 350 km2
(86,500 acres) of coastal forests and hills in the Santa Cruz Mountains
region (Red outline in right figure; Santa Cruz and San Mateo counties,
California). Among the watersheds severely affected by wildfire was
Scott Creek (Yellow outline in right figure), a small (70 km2) coastal
basin \~80 km south of San Francisco Bay. The Scott Creek watershed is
of special management concern as it supports the southernmost extant
population of coho salmon (*Oncorhynchus kisutch*; Central California
Coast \[CCC\] evolutionarily significant unit) in North America, as well
as federally threatened CCC steelhead (anadramous *O. mykiss*). Scott
Creek is also the location of a salmonid life cycle monitoring station
operated jointly by NOAA’s Southwest Fisheries Science Center ([FED
project
website](https://www.fisheries.noaa.gov/west-coast/science-data/landscape-and-seascape-ecology-research-california-salmon))
and the University of California, Santa Cruz Fisheries Collaboration
Program ([FCP project
website](https://fisheries.ucsc.edu/research-teams/scott-creek/)).
Extensive physical, chemical, and biological monitoring conducted
throughout the Scott Creek watershed since 2002 provides a unique
opportunity to rigorously examine the direct and indirect effects of
wildfire on salmonid productivity and carrying capacity.

<img align="Right" width="300" height="200" src="Figures/Lagoon_lookingUS_20211130.jpg">

Water Year 2022 (WY22) brought multiple mass wasting events and flushing
flows which brough large amounts of sediment into the creek. We believe
this sediment filled in pool habitat (reducing pool quantity, pool
volume, and maximum pool depth). We also suspect sediment reached the
Scott Creek Estuary/Lagoon; filling in areas of depth and simplifying
the channel bed (right figure shows fine sediment deposition in the
estuary 30 November 2021). This repository focuses on data collected in
the Scott Creek Estuary/Lagoon and a separate repository is dedicated to
the [pool sediment survey
data](https://drive.google.com/drive/u/1/folders/1GPUKNrafZbOOjcCcR4sZtiPQt50azaap).
Our goal was to survey the lagoon habitat using RTK GPS and create a
bathymetric surface. Ultimately we hope to track how this habitat
changes over time and answer the question “How much has the Scott Creek
estuary/lagoon filled in with fine sediment compared to pre-fire
conditions?”.

# Readme File Purpose

This readme file consists of an overview of the datasets, goals, and
data visualizations used in the XXXX. The goal was to \[Add more details
here\].

<br>

# Workflow Summary

The general workflow is:

1.  Collect topo and echo sounder points.

2.  Extract data from the R10s (L. Harrison helped with this) and
    correct raw data with OPUS output.

3.  Correct echosounder point depths to account for “draft”.

4.  Remove bad topo points and echo points that are too shallow or have
    low accuracy.

5.  Calculate bed surface elevation (BSE) from echosunder points (Note:
    topo points are corrected in step 2).

6.  Calculate WSE from topo points.

7.  Join topo and echosounder BSE points.

8.  Convert BSE points into TIN layer(in ArcMap).

9.  Convert TIN to raster layer (in ArcMap).

10. TBD - Compair WY22 layer to ESA Dec 2016 layer. Raster or TIN
    differencing (in ArcMap? or R?).

<br>

## Dataset Descriptions

The <span style="color:purple">*Data*</span> folder contains the rtk
datasets used…

1.  The <span style="color:purple">*XXX.csv*</span> datafile consists of
    XXX.

<br>

# 1. Fieldwork Notes

On 30 August 2022, the Scott Creek crew surveyed the lagoon habitat with
three RTK units (Trimble R10’s). Each unit has its own raw data file
(desribed above) which are used in the workflow (steps above).

-   Survey Units: US Survey Ft;

-   Horizontal Datum: US State Plane NAD83 CA Zone 3

-   Vertical Datum: Conus GEOID12A.

-   Survey extent: Scott Creek State Beach inland to Queseria Creek
    confluence. Most topo points were collected from the beach to the
    north marsh area (bad signal starting around the Lagoon PIT antenna
    array). Echosounder points focused on the main channel from the
    beach (downstream side of Hwy 1 bridge) to Queseria Creek
    confluence.

-   Blue Unit - Base station.

    -   Settup on ESA CP02 and ran for 8 hours (for OPUS correction).
    -   Antenna height to quick release = 4.130 ft (1.5m).
    -   Job Name: sc_blue_220830.

-   Green Unit - Rover collecting topo points

    -   Antenna height to quick release = 6.560 ft (2.0m).
    -   Job Name: sc_grn_220830.
    -   Shot to ESA CP01 for check point. Found an unknown control point
        (code = CPX) on North Marsh near Hwy 1.
    -   Started topo survey at point \#5.
    -   Raw Data Corrections:
        -   Change point code from WSE to topo for points 108,109, 163,
            and 164.
        -   Delete points 337 and 345.
    -   At point 334 we focused on WS Edge points and used a single rod
        (antenna height to quick release = 3.42 ft). Note WSE points
        using the short rod are at the water surface but were up to 0.5
        ft from the actual bank (vegitation was blocking signal so X,Y
        coordinates are close but not exact).

-   Red Unit - Rover collecting echosounder points (Sonarmite; wet areas
    with depth).

    -   Antenna height to quick release = 4.130 ft.
    -   Job Name: sc_red_220830.
    -   Sounder depth in water (a.k.a. “Draft”) = 0.651 ft
    -   Started at point number 1000 with code = echo. Collected
        \~12,000 points.

-   Survey Codes:

    -   levee - top of levee.
    -   topo - compination of wet and dry topographic points.
    -   rock - armouring at Hwy 1 bridge (“Jacks”)
    -   wse - Water Surface Elevation at the edge of bank (transition
        from wet to dry).
    -   echo - wet echosounder point (need to incorperate depth
        measurments to elevation to get BSE).

-   The North Marsh was wet dueing the survey (pre-fire times this was
    rare in the summer). Perhapse this is because the sandbar formed at
    a typical elevation and the lagoon was filled in with sediment so
    the water went on the marshplain.

# 2. OPUS Correction

(raw base station file submitted to OPUS and then apply correction to
all points)

3.  Correct echosounder point depths to account for “draft”.

4.  Remove bad topo points and echo points that are too shallow or have
    low accuracy.

5.  Calculate bed surface elevation (BSE) from echosunder points (Note:
    topo points are corrected in step 2).

6.  Calculate WSE from topo points.

7.  Join topo and echosounder BSE points.

8.  Convert BSE points into TIN layer(in ArcMap).

9.  Convert TIN to raster layer (in ArcMap).

10. TBD - Compair WY22 layer to ESA Dec 2016 layer. Raster or TIN
    differencing (in ArcMap? or R?).
