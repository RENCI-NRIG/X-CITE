# FAIR Data - Better Science Through Data Sharing

Wouldn't it be great if you could quickly find data generated from
other people's experiments, combine it with your own data, and produce
new, high-value output? Wouldn't it be even better if other people
could discover your data, utilize it, and cite your data in their
papers? That is precisely the goal of FAIR Data - making results
Findable, Accessible, Interoperable, and Reusable.

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
fully-documented, unencumbered protocol that (optionally) allow for
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
except it's only readable by a program that only runs on a 25 year old
version of MacOS. Yes, that really happens. If we design our
(meta)data for interoperability then we can take that 25+ year old
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
Framework (RDF). We'll talk more about this in a later section.

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
metadata can be really simple or it can be really complicated. Where
it falls on that continuum is situational. Small amounts of simple
data will probably have simple metadata

### What Metadata is and why we care

### Metadata representation and searching

#### JSON

#### RDF

### The future: AI-generated Metadata

## FOXDEN - a Pilot, Prototype Example

FOXDEN (FAIR Open-Science Extensible Data Exchange Network) is a
preliminary implementation of a data management system that can be
used to meet the FAIR requirements. The system gets inspiration from
Linux, in that it provides a collection of tools that work together in
a modular fashion. It is possible to use all or some of the components.

Access to the FOXDEN modules is via either a web page for each module
or by using a command-line tool. The comma