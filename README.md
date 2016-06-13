# Beacon-on-GA4GH-API

##Contents

* [What it is](#what-it-is)
* [System requirements](#system-requirements)
* [How to run it](#how-to-run-it)
* [How it works](#how-it-works)
* [Technologies](#technologies)

Note that much of this code springs from the original Beacon python starter kit found at https://github.com/mcupak/beacon-python

##What it is
This project contains code that runs a flask Beacon service that uses the GA4GH APIs to fill in the Beacon requests. Note that this code has been modified to run against the 1kgenomes.ga4gh.org server. Pointing at a different server should be simple,

##System requirements
All you need to build this project is Python and Flask web framework. If you're running Linux, OS X or Windows with cygwin support, the following commands should be enough to set up Flask (the process is a bit different with the native version of Python on Windows):

    $ cd todo-api
    $ virtualenv flask
    $ flask/bin/pip install flask
    $ flask/bin/pip install ga4gh

##How to run it
Launch beacon.py:

    $ chmod a+x beacon.py
    $ ./beacon.py

This starts an embedded server. By default, the application will be available at <http://127.0.0.1:5000>

##How it works
Modify the beacon2ga4gh.cfg file to signify the URL for your GA4GH compliant server

The code takes care of the rest and provides the following endpoints when you start your beacon:

    http://127.0.0.1:5000/beacon/info - information about your beacon
    http://127.0.0.1:5000/beacon/query - access to query service
    http://127.0.0.1:5000/beacon/ - basic welcome message with sample query

Query examples:

    http://127.0.0.1:5000/beacon/query?referenceName=chr17&start=35098007&alternateBases=A&assemblyId=NCBI37

Possible parameters for query:

   referenceName - Which chromosome (i.e. 17 or chr17)
   start - 1-based position on the chromosome to check
   alternateBases - singe or multiple bases to search for
   assemblyID - Which reference to use (i.e. NCBI37)
   referenceBases - bases being replaced by the variation *Ignored for now*
   includeDatasetResponse - boolean to request an array of returns, one for each variant that matches *Hard set to True for now*
   datasetIds - IDs of the data sets to search *not implemented yet*

##Technologies
Python, Flask.
