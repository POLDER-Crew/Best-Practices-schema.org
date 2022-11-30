## Table of contents
1. [INTRODUCTION](#Introduction)
   * [1.1 Related activities in the schema.org community](#related-activities-in-the-schema.org-community)
   * [1.2 Polar data discovery as a use case](#polar-data-discovery-as-a-use-case)
2. [GETTING STARTED](#getting-started)
   * [Content Includes](#Content Includes)
3. [STEP-BY-STEP](#methods)
   * [Content Includes](#Content Includes)
4. [Modifying](#modifying)
   * [Content Includes](#Content Includes)
5. [TROUBLESHOOTING/COMMON ERRORS](#troubleshooting/common errors)
   * [Content Includes](#Content Includes)
6. [CONCLUSION](#conclusion)
   * [Content Includes](#Content Includes)
7. [REFERENCES](#references)
   * [Content Includes](#Content Includes)
8. [APPENDIX](#appendix)
   * [Acronyms](#acryonyms)
   * [Terms](#terms)

# 1. Introduction <a name="Introduction"></a>

Previous experience with implementing metadata standards in the polar data management community has demonstrated that there are as many ways to write metadata as there are metadata authors. The end result of many parallel metadata writing efforts is difficulty in brokering the various flavours of each metadata standard. With schema.org (SDO) being a relatively young technology in the scientific data management field, we have the opportunity to collectively agree on some core principles of best practice before too many data centres have implemented it. Semantic markup is a core technology the research data management community has at our disposal. Adopting semantic markup and related technologies assists in automating our workflows. If you are new to the schema.org realm, there is a ‘Schema.org for Research Data Managers: A Primer’ (Payne, K., & Verhey, C., 2022) that was created to lay out the SDO landscape, where it came from, what is driving its uptake in research data management, and how it works in broad strokes. It was designed to introduce individuals with little technical knowledge to the benefits and importance of schema.org. It is aimed to be a ‘one-step-back’ to help set the landscape and equip you to better understand the various ‘Best Practices’ documents throughout the RDM community. 

## 1.1 Related activities in the schema.org community <a name="related-activities-in-the-schema.org-community"></a>
 There are numerous initiatives currently working to harness the benefits of schema.org and produce valuable resources for others to follow suit. Many of these have informed POLDER’s deliberations and therefore provide important context for this document. A few of these are described in the paragraphs below.

DataONE is a global community-driven network for harvesting schema.org and other structured metadata models to provide aggregated data services, including spatial, temporal, and semantic search, metadata FAIR reports, and data citation reports, all within customizable data portals (see https://search.dataone.org/portals/polderdemo/).

Science-on-schema.org (SOSO) is an Earth Science Information Partners (ESIP)-led cluster providing guidance for publishing schema.org in JSON-LD to the science community. Currently, the group has released the V1.3 set of their recommendations that help describe Datasets and Data Repositories. The science-on-schema guides include examples for ‘variableMeasured’, ‘funding’, ‘identifier’ and many more. 

The United Nations has declared the 2020s to be the  United Nations Decade of Ocean Science for Sustainable Development (UNDOS). The UNDOS Task Force has identified scientific priorities, including six cross-cutting challenges relevant to the data community, including “ensur[ing] capacity development and access to knowledge; Improv[ing] interdisciplinary capacity and knowledge integration; and facilitate[ing] transnational cooperation and complementarity”. In response to these challenges, the Ocean Info Hub (OIH) was created. The OIH uses the gleaner.io tool that extracts JSON-LD from web pages. The OIH provides Gleaner with a list of ocean repositories to index and it will access and retrieve pages based on the sitemap.xml of the domain(s). Gleaner can then compile the information into a form usable to drive a search interface. 

NASA’s International Directory Node (IDN), formerly known as the Global Change Master Directory (GCMD), has played a critical role in the development of the Antarctic data management community. The IDN underpins both the Antarctic Master Directory (AMD) and the Southern Ocean Observing System’s (SOOS) metadata portal. The AMD presents all records in the IDN that were contributed by National Antarctic Data Centres, and contains a mix of unique records that were uploaded directly to the IDN and duplicates of records held by the NADCs. The AMD has been the key element around which the Standing Committee on Antarctic Data Management (a body of the Scientific Committee on Antarctic Research) has organised its data management activities over the past two decades. The SOOS metadata portal is a subset of all IDN holdings that overlap the geographic region below 40S, include keywords associated with oceans or coast, and with a few specific exclusions to remove terrestrial and sociological data.. The IDN has implemented schema.org as part of its ongoing development activities. 
The Alaska Data Integration Working Group (ADIwg) pursued a related effort to share metadata through an ISO 19115/19110 compatible JSON standard. ADIwg published a GitHub archive to share schema documentation, an editor and translation tools. The US Fish and Wildlife Service’s Science Applications Program, the US Geological Survey (USGS) and the US Bureau of Ocean Energy Management have continued to work in partnership to utilise this community adoption to describe projects and datasets. The USGS Alaska Science Center has also been working to include descriptions of collections of sampling sites (with expertise from ISO specialist Ted Habermann). The Arctic Research Mapping Application and Arctic Observing Viewer were early adopters of ADIwg’s community specification for ISO XML and will continue to provide access to information for NSF projects through a new Arctic Operations Gateway API endpoint.
Several Interest and Working Groups of the Research Data Alliance (RDA) are focused on a range of metadata issues, including those pertinent to data discoverability, access, and interoperability. These groups include the Metadata Interest Group, Brokering Framework Working Group, Metadata Standards Catalog Working Group, and the Research Data Repository Interoperability Working Group. Of particular note is the set of guidelines published by the RDA Research Metadata Schemas Working Group. These guidelines do not advocate for any particular metadata schema when implementing schema.org, but instead are intended to ensure the consistent application of schema.org markup regardless of data source, and thus improve data discoverability over the long term.

The Canadian Consortium for Arctic Data Interoperability (CCADI) is an initiative to develop an integrated Canadian Arctic data management system (distributed) that will facilitate information discovery, establish sharing standards, enable interoperability among existing data infrastructures, and that will be co-designed with, and accessible to, a broad user base.  The CCADI team is co-designing and implementing a multi-tiered architecture that includes establishment of metadata, data, vocabulary, media and other information services. Individual CCADI member centres are implementing schema.org metadata publication tools guided by POLDER best practices. To support integration of metadata from different sources, crosswalk ontologies and a semantic mediator are under development. Standardised metadata will be served to end users through a metadata  aggregator developed and hosted by the Polar Data Catalogue.  Metadata and data services will be released throughout 2022.

WC3 provides a best practices document which can be found at https://www.w3.org/TR/dwbp/ . Section 8.2 recommends the following descriptive metadata fields: 
The title and a description of the dataset.
The keywords describing the dataset.
The date of publication of the dataset.
The entity responsible (publisher) for making the dataset available.
The contact point for the dataset.
The spatial coverage of the dataset.
The temporal period that the dataset covers.
The date of last modification of the dataset.
The themes/categories covered by a dataset.
The title and a description of the distribution.
The date of publication of the distribution.
The media type of the distribution.

## 1.2 Polar data discovery as a use case <a name="polar-data-discovery-as-a-use-case"></a>

There are a wide range of use cases for including schema.org metadata on data landing pages.  These range all the way from simply having your data show up on Google's Dataset Search to supporting the development of very advanced domain specific data discovery, access and analysis clients.  Here the goal is intermediate between these two extremes - "To support the development of a federated polar data discovery portal", referred to hereafter as Polar Federated Search. Polar Federated Search is conceived as a single point of access that allows users to perform basic searches (text, time, space) on metadata records held in a large number of data catalogues that host polar-relevant data. 

A note on scope: What do we mean by polar data? 
Polar data is widely disparate in terms of formats, topics, and the people and institutions that collect them.  Numerous forms of traditional knowledge are considered data.  One example is the Inuit tactile driftwood maps with carved nobs and notches used to represent capes, islands, and inlets on the Greenlandic coast (see figure 1 below). Geographically, POLDER represents data managers working in the Arctic, Antarctic, and Southern Ocean. The latitudinal boundaries for these regions vary between institutions. This document refers to polar data as any data within the polar region. The polar region will be defined as above 50 degrees latitudinal north in North America, Scandinavia, Asia; 60 degrees latitude north in Europe and below 40 degrees latitude south in the southern hemisphere (acknowledging that this rough guide includes the southern tips of continents not usually thought of as polar)  (Verhey, C., Minch, M., Payne, K., & PPFS Advisory Team, 2022). 

Figure 1: Inuit tactile driftwood map. Lightweight, made for kayak travel, specific to -feel- rather than sight (pictured above) Source: (Jakobsen, 2000)                         














# Required fields:
...

# Optional fields:
... 

#Examples:
- samples
- models
- data streams
- interviews
- stories
