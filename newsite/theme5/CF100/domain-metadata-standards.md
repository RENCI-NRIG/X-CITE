# FAIR Data - Better Science Through Data Sharing

[![XKCD 1805: Unpublished Discoveries, © Randall Munroe, Creative
Commons Attibution-NonCommercial
license](unpublished_discoveries.png)][xkcd-discoveries]

[xkcd-discoveries]: https://xkcd.com/1805/
[by-nc]: https://creativecommons.org/licenses/by-nc/2.5/



Wouldn't it be great if you could quickly find data generated from
other people's experiments, combine it with your own data, and produce
new, high-value output? Wouldn't it be even better if other people
could discover your data, utilize it, and cite your data in their
papers?  That is precisely the goal of FAIR Data - making results
**F**indable, **A**ccessible, **I**nteroperable, and **R**eusable.
Originally introduced in the article titled _[The FAIR Guiding
Principles for scientific data management and
stewardship][fair-paper]_ in 2016, these principles have become a
fundamental framework for scientific data management and stewardship.

In this section of the X-CITE training materials, we'll look at the
motivations behind FAIR, take a more detailed look at each of the four
components, and consider some of the implications of these large-scale
sharing principles.

## Why FAIR?

Running experiments and collecting data is expensive [citation
needed]. Funding agencies don't want to pay for running the same
experimental design over and over beyond, perhaps, a replication
study. Publishers are looking for new ways to add value to their
curation of articles. And most importantly (to us, at least) there are
the researchers who are producing these voluminous datasets.

Individual researchers have their own needs for FAIR. Speed is a big
one - having Findable and Accessible data already available can lead
to faster hypothosis formation, allow earlier grant proposals, and
establish priority in publication. A second concern is
publication. Historically it wasn't easy to publish raw data because
it's expensive to keep and grants wouldn't pay for it. There are
repositories now where your experimental data can be stored and
accessed. Some of them are very domain specific (such as Cornell's
FOXDEN, which we look at later) and others are designed more for
"general purpose" use. Finally, adhering to the FAIR Data principles
makes it easy (and expected!) for other researchers using your data to
cite your work with unambiguous credit and with a permanent network
location where the material can be found. FAIR is not restricted to
data in the historical sense, but also encompasses source code and
workflows.

Publishers stand to benefit from FAIR, especially if they take full
advantage of the ideas. Findable and Accessible (not to mention
Interoperable and Reusable) data leads to it being used more and by a
wider distribution of users. Researchers in one field probably don't
read journals in a different one. But what if that outlier of a
researcher was able to discover data relevant to their work? Now the
publisher may have a broader market to sell into. Discoverable data
doesn't come from outer space, with apologies to the astronomers, but
is a product of research and that research is accompanied by
publications. Publishers will barely care if the underlying data is
cited, but they care deeply that the associated journal articles
are. FAIR principles, through the "side effect" of increasing
publication citations, boost the Impact Factor for journals and that
benefits both the authors and the publisher.

## The Principles of FAIR-ness

Findable, Accessible, Interoperable, and Reusable.

In this section we will look at the aspects that make up each of
Findability, Accessibility, Interoperability, and Reusability. As you
read this, keep in mind that the principles are *descriptive* rather
than *prescriptive*. There is no attempt to describe *how* to
implement an archive, for instance, but rather to discuss what the
requirement is and leave the implementation details up to the
implementers.

### Findable

The first requirement for a data set to be useful is for it to be
findable. If no one can find it, it may as well not exist. There has
to be some kind of automatic way to describe what you are looking for
and get a list of possible results in return. If this sounds like a
Search Engine, then you're on the right track. Search engines are
pretty good at what they're designed for, which is hunting through
immense collections of text and determining which documents are
statistically likely to be useful. The problem is the "collections of
text" part: general-purpose search engines have little or no
conception of structured data. Imagine trying to search for
spreadsheets that contain bond angle data and find the ones that have
particular angles, in a particular order, under specific
circumstances. Clearly, we're going to need something more versatile
than just a text search engine (sorry, Google).

There are four elements that make up the "Findable" principle:

* F1. (meta)data are assigned a globally unique and persistent identifier
* F2. data are described with rich metadata (defined by R1 below)
* F3. metadata clearly and explicitly include the identfier of the data it describes
* F4. (meta)data are registered or indexed in a searchable resource

Looking at these elements, we see that there must be rich metadata
available to describe a data set well enough to facilitate people
finding the (meta)data, and both the data itself as well as the
metadata need to be published in a way that facilitates indexing
both. The data and metadata must each have a Globally Unique
Identifier - think of it as being like a URL. If you have already seen
"doi:" used to refer to journal articles, then it will come as no
surprise to see this extended to (meta)data.

### Accessible

Moving on to "Accessible", let's take a look at what goes into that:

* A1. (meta)data are retrievable by their identifier using a standardized communications protocol
* A1.1 the protocol is open, free, and universally implementable
* A1.2 the protocol allows for an authentication and authorization procedure, where necessary
* A2. metadata are accessible, even when the data are no longer available

There are two basic aims here. The first is to use a well-known,
fully-documented, unencumbered protocol that (optionally) allows for
authentication and authorization tasks ("logging in") to be
completed. The last aim is unexpected at first blush but makes sense
when you think about it: metadata live forever, even after the data
they describe has finally been deleted. Permanently keeping the
metadata as a record of what work has gone before makes it possible to
get an idea of past research directions. Interestingly, "mining"
collections of metadata can produce new knowledge of its own.

### Interoperable

Interoperability simply means that the data are sufficiently described
by their metadata so that researchers can create their own tools, or
use the tools of others, to work with the data without having to use
the same software as the original researcher. Very importantly, if at
all possible the data should be preserved in a way that doesn't
require the use of proprietary software to read it. This is not simply
because of cost, though that can be a major barrier, but is also a
matter of historical preservation - it may be impossible to locate or
run old enough software. Imagine having a really useful data set
except it's only readable by a program that only runs on a 35 year old
version of MacOS. Yes, that really happens. If we design our
(meta)data for interoperability then we can take that 35+ year old
dataset and work with it using modern tools.

* I1. (meta)data use a formal, accessible, shared, and broadly applicable language for knowledge representation.
* I2. (meta)data use vocabularies that follow FAIR principles
* I3. (meta)data include qualified references to other (meta)data

The first of these elements is a challenge, honestly. The goal is to
have a very rich way of representing metadata that preserves the
semantics of the metadata. It's not enough to simply say "the third
column is conductance". What is needed is a way to say "the third
column is conductance, it's an electronic measure, it's related to
resistance, and here is how". It's a lot of work, but luckily for us
most of it has been done and we can reuse it - Resource Definition
Framework (RDF) is made for this job. We'll talk more about this in a
later section.

### Reusable

R1. meta(data) are richly described with a plurality of accurate and relevant attributes
R1.1. (meta)data are released with a clear and accessible data usage license
R1.2. (meta)data are associated with detailed provenance
R1.3. (meta)data meet domain-relevant community standards

The crux of this principle is ensuring high-quality curation. The
metadata should be thoroughly descriptive and will indicate, among
other things, the rights the authors has granted to future users and a
"chain of custody" that describes how the (meta)data came to
be. Finally, the (meta)data should of course be of high quality to
begin with, in line with the standards of the discipline. If you are
dealing with human subjects, be aware that data privacy requirements
(HIPPA, IRB) may restrict or prohibit the publication of data and even
metadata. Enough metadata can sometimes be used to reconstruct the
data itself. As an example, sometimes age, zip code, and gender is
enough to identify someone - some zip codes have very people in
them. 28520 has about 250 people.

## Metadata

As mentioned above, metadata is simply information that describes your
data. Hidden behind that word "simply" is the slight complication that
metadata can be anything from really simple to really complicated. Where
it falls on that continuum is situational. Small amounts of simple
data will probably have simple metadata.

### Metadata representation and searching

Without a standard means of representation and agreed-upon meanings,
the metadata we assemble might be more of a hinderance than a
help. Selecting our data's properties to record is domain-specific in
many cases. A very general set of attributes is available at
[schema.org](https://schema.org/). Other ontologies exist, of course,
and selection among them tends to narrow as you go.

#### RDF

RDF is "Resource Description Format" and is a broadly used concept
even outside of FAIR. Fundamentally, RDF's "intention" is to describe
the world in terms of triples: subject, predicate, and object. From
these building blocks we can construct graph structures (in the
"discrete math" sense of the term). As they grow, they can represent
linkages between related items, for instance, and that is when the
real power of RDF can start to be exploited. With small collections of
metadata there is little choice but to handle search terms, for
instance. Once the collection expands, new kinds of queries are
possible. For instance, different researchers might submit data to an
archive. We know the possible range of metadata descriptors and we
know what each one means. At this point, we can traverse the RDF
graph. It's easy to go from the starting place to enter the graph and
then follow along, hop by hop, expanding the search possibilities by
adding related terms.

#### JSON and JSON-LD

For any data to be useable by a computer, it has to be represented in
a way that it can be understood. Metadata is no exception. RDF is both
a conceptual layout for in-memory processing and also a defined way of
writing out the structure. There are just two problems. One is that
the format is a lot to digest when you first start working with
it. The other is that, depending on the language you're using, you
might end up having to write your own parser for this. Luck is smiling
on us, though, in the form of alternative ways to represent that graph
structure. A very common representation, and one that is becoming
increasingly popular, is JSON (Javascript Object Notation). It has its
roots in Javascript, but it has spread far and wide in dozens of
languages. Support for it is nearly ubiquitous now. Take a look at it.

```
{
  "first_name": "John",
  "last_name": "Smith",
  "is_alive": true,
  "age": 27,
  "address": {
    "street_address": "21 2nd Street",
    "city": "New York",
    "state": "NY",
    "postal_code": "10021-3100"
  },
  "phone_numbers": [
    {
      "type": "home",
      "number": "212 555-1234"
    },
    {
      "type": "office",
      "number": "646 555-4567"
    }
  ],
  "children": [
    "Catherine",
    "Thomas",
    "Trevor"
  ],
  "spouse": null
}
```

JSON is good for representing lots of structured data, but there needs
to be something that can go beyond that and hold references to the
schemas that apply to certain fields. For this, there is JSON-LD. The
LD stands for "Linked Data". JSON-LD stores additional data in the
form of "context" fields and these fields can contain URLs to outside
sites storing official, curated ontologies:

```
{
  "@context": "https://json-ld.org/contexts/person.jsonld",
  "@id": "http://dbpedia.org/resource/John_Lennon",
  "name": "John Lennon",
  "born": "1940-10-09",
  "spouse": "http://dbpedia.org/resource/Cynthia_Lennon"
}
```

## FOXDEN - a Pilot, Prototype Example

FOXDEN (FAIR Open-Science Extensible Data Exchange Network) is a
preliminary implementation of a data management system that can be
used to meet the FAIR requirements. The system gets inspiration from
Linux, in that it provides a collection of tools that work together in
a modular fashion. It is possible to use all or some of the components.

Access to the FOXDEN modules is via either a web page for each module
or by using a command-line tool. Besides being a perfectly reasonable
way to use the tools, the command line tool is also well suited to use
in scripts.

### The Modules

FOXDEN's modular architecture makes it easy to select which components
of it you'd like to use and even makes it possible to substitute your
own software if you have specialized needs. The FOXDEN documentation
has a walkthrough of basic use. This document will instead give some
brief background on each component. You're encouraged to work through
the "Quick Start Guide".

#### Frontend service: web interface

As you would (likely) expect, the Frontend service generates the web
pages through which users can easily interact with the
system. Initially, the user is presented with a login page. Once past
that, access to the other modules is a click or two away. Of
particular interest is the "docs" button toward the upper-right
corner. Having the documentation close at hand will prove... handy.

#### Command line (CLI) tool

The command line tool ("foxden") is both an alternative way users can
access the system as well as a means to interface shell scripts to the
system for automating common tasks. The "foxden" command by itself
with no arguments will display a list of the available commands and
also gives a link to the documentation and a reminder of how to get
more detailed help.

#### Authentication and authorization service

Even in a purely open research environment, it's still necessary to
keep track of who is making changes. This is both for proper
attribution as well as non-repudiation (perhaps less of a factor in
X-Ray Science than in other disciplines, but the system is built to be
versatile). Web users will see a familiar-looking login screen. CLI
users will need to authenticate via Kerberos - don't worry, it's well
described in the introductory documentation. FOXDEN mercifully
provides a way to use Kerberos that is simpler than the old-school
way.

#### Data Discovery service

The Discovery service provides a way to query the underlying
"management database" that tracks movement of files and the metadata
associated with them. The query language is the same one MongoDB used
(Mongo QL).

#### MetaData service

The MetaData service is one of the critical components. This module
can not only query metadata, for instance finding matching schemas,
but also create new schemas and manipulate existing ones.

#### Provenance service

The Provenance service provides a lot of functionality. The tracking
of "provenance" is not just something art historians do. The term
refers to the tracking of every movement of the data we're managing,
what tools were used to transform it and under what circumstances, and
where the data came from. This last element could be, say, "from this
instrument on this beamline" or it could be "Dr. J. Doe's Sept 13th
dataset, reduced by this lump of MATLAB code".

#### Data Management service

The Data Management service abstracts data movement in and out of the
underlying Object Store (AWS S3 or compatible). Functions are provided
to both manage the Object Store as well as to move data in, move it
out, or delete it.

#### Publication service

The Publication service has two major sections. The first handles the
creation and assignment of DOIs (Document Object Identifiers - you've
seen these in "References" sections) and the association of that
identifier with metadata and data. The second section provides a means
to interact with Zenodo in a manner consistent with the rest of
FOXDEN.

#### SpecScan service

SpecScan is pretty specific: it is used to create and manipulate
records for spec scans. It does what it says on the tin.

#### MLHub

The MLHub service allows the user to run various Machine Learning (ML)
algorithms directly in the FOXDEN environment. TensorFlow is directly
supported. Doing this directly inside of FOXDEN seems odd at first,
but it follows the paradigm of "moving the compute to the data",
preventing time-consuming retrievals.

#### CHESS Analysis Pipeline (CHAP)

The CHAP service simplifies running the CHESS-developed CHAP algorithms on data stored in FOXDEN. 

#### CHAP Notebook

Designed for novice programmers, the CHAP Notebook service simplifies
data analysis by giving users a Jupyter-like interface for writing
code modules that are inserted into pre-defined workflows. These
modules are also deposited in a code repository for future
dissemination.