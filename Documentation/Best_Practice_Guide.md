# Introduction:
## Why a guide is needed

Previous experience with implementing metadata standards in the polar data management community has demonstrated that there are as many ways to write metadata as there are metadata authors. The end result of many parallel metadata writing efforts is difficulty in brokering the various flavours of each metadata standard. 

With schema.org being relatively young technology in the scientific data management field, we have the opportunity to collectively agree on some core principles of best practice before too many data centres have implemented it. 


## The use case (discovery) we are trying to solve

There are a wide range of use cases for including schema.org metadata on data landing pages.  These range all the way from simply having your data show up on Google's Dataset Search to supporting the development of very advanced domain specific data discovery, access and analysis clients.  Here the goal is intermediate between these two extreme's - "To support the development of a federated polar data discovery portal".

# Background:
- who is doing what where....

# Required fields:

For the federated polar data discovery portal, the required fields (beyond those needed to support Google's Dataset Search - described somewhere else) are:

- Temporal coverage
- Spatial coverage
- Parameters/Variables Measured

## Temporal coverage:

### General Considerations:

See [SOSO temporal coverage](https://github.com/ESIPFed/science-on-schema.org/blob/master/guides/Dataset.md#temporal-coverage) for details of the Science on schema.org (SOSO) guidance on this topic.

#### Guidance

- Uncontrolled plain text date strings are not allowed (e.g., just say NO to "January 20, 2017")!
- Similarly, uncharacterized URLs are also not allowed; but at this point SOSO has not yet agreed on a standard way to allow structured temporal identifiers; so hold off on using them or be prepared to change the way you are doing this when SOSO finalizes their recommendations.

### Dynamically updated datasets

In many catalogs currently, datasets are listed as ongoing, yet their end dates are never updated once collection ends.  This thoroughly confuses searches.  Our recommendations are:

#### Guidance

- Repositories need to update the end date routinely, though not more often than once per day
  - Fundamentally this means that if you are automatically updating your data, you should be automatically updating its metadata as well!

### Discontinuous, cyclical or seasonal data

Seasonal data are important for many environmental questions and discontinuous time ranges are common in many kinds of data (e.g., intermittent data gathering eforts).  As a result, representing these discontinuous time ranges is important.  While schema.org allows for associating multiple time ranges (or actually most properties) to an oject such as a dataset, seasonal names (e.g., moose season, winter, breakup) can't be easily turned into time ranges, so don't use them unless there is an ontology available (perhaps you created it?) that define them as time ranges.  In that case use the SOSO recommendation for doing so (when it exists)...

#### Guidance

- A dataset with discontinuous time ranges, should have multiple temporal coverage records - one for each time range
- Don't use seasonal names unless there is an existing ontology defining them available.
- Use SOSO recommendations for associating the name to its ontology definition.
 
### Uncertain dates

In many collections, the temporal coverage of a dataset may be uncertain.  For example, a scrapbook of photos from the Arctic may be identified only to within a decade or two.  

#### Guidance

- If having those data show up in a search which includes temporal criteria is important to your repository please include the presumed date range in your markup.

For example, if the scrapbook of Arctic photos were from the 1950's it's temporal coverage could be described as:

<pre>
{
  ...
  <strong>"temporalCoverage": "1950/1960"</strong>
}
</pre>

### Deep time and Chronometric dates

While supporting deep time and chronometric dates is generally agreed to be important for our use case, we agreed to wait for SOSO to finalize their advise before adding anything here.

## Spatial coverage

### General considerations

See [SOSO spatial coverage](https://github.com/ESIPFed/science-on-schema.org/blob/master/guides/Dataset.md#spatial-coverage) for details of the Science on schema.org (SOSO) guidance on this topic.

Bounding boxes are quite problematic for describing data in polar regions, especially for data that cover both poles (but not the equator), for scattered sites, ship or bouy tracks, etc.  While for a basic Google Dataset Search, a point or bounding box is good enough, for this use case a list of GeoShapes or GeoCoordinates is necessary, especially to enable the I in FAIR!

#### Guidance

- Use a list of GeoShapes or GeoCoordinates for your spatial coverage

### Place names

Where place names are associated with detailed spatial boundaries (e.g., administrative boundaries, watersheds, etc.), these may often provide much better query results than a roughly drawn polygon, which may hit multiple defined places inadvertantly.  However, purely human-readable names, without detailed spatial boundaries are effectively useless for searching.  

#### Guidance

- The schema:name property should be used for the human-readable name of a place
- Follow SOSO guidelines for associating place names with their detailed spatial boundaries in existing controlled vocabularies/gazetteers

# Optional fields:
... 

# Examples:
- samples
- models
- data streams
- interviews
- stories
