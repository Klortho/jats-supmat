The extension is described in the paper [Extending JATS to include the NISO/NFAIS
Recommended Practices for Online Supplemental Journal Article
Materials](http://www.ncbi.nlm.nih.gov/books/NBK159734/), by Karen Gutzman and Kimberly A. Tryka,
presented at [JATSCon
2013(4)](http://jats.nlm.nih.gov/jats-con/2013/schedule2013.html).

The files for this extension are currently deployed [here](http://dtd.nlm.nih.gov/ncbi/supmatext/),
and those were used to seed this GitHub repository.

This extension is is a working draft, and is *not final*.  Please work with us to help us make it is good as it can be.

Please use the [Issues](https://github.com/Klortho/jats-supmat/issues) here to bring up and
discuss use cases, problems and changes.

# Working environment

The instructions here are for downloading this tag set and setting up an environment for
working on it.  They are specific to Unix or Mac, but Windows should work just as well.
It assumes you have `xmllint` installed, which comes as part of [Libxml2](http://xmlsoft.org/).

```
# Get this repo
git clone https://github.com/Klortho/jats-supmat.git
cd jats-supmat

# Get the JATS Archiving and Interchange DTD, version 1.0
mkdir jats-archiving-dtd-1.0
cd jats-archiving-dtd-1.0
wget ftp://ftp.ncbi.nih.gov/pub/jats/archiving/1.0/jats-archiving-dtd-1.0.zip
unzip jats-archiving-dtd-1.0.zip
export XML_CATALOG_FILES=`pwd`/catalog-test-jats-v1.xml
cd ..

# Get the DtdAnalyzer, and add it to your PATH
wget http://dtd.nlm.nih.gov/ncbi/dtdanalyzer/downloads/DtdAnalyzer-0.4.zip
unzip DtdAnalyzer-0.4.zip
export PATH=$PATH:`pwd`/DtdAnalyzer-0.4

# Validate a sample file
cd samples
xmllint --valid --noout Adiposity-ext.xml
cd ..

# Generate the documentation
dtddocumentor -c $XML_CATALOG_FILES dtd/NISO-supmat-extension-rec0.dtd
```

Note that to view the documentation, you have to serve the generated `doc` folder from
an HTTP server, and open that in your web browser.
The documentation for the latest version of this repo is currently served at
[http://jatspan.org/jats-supmat/doc/](http://jatspan.org/jats-supmat/doc/).
