## Notes from IIIF Workshop

### Session 1

#### Presentation - Benjamin Albritton

- IIIF; Roman de la Rose Project and a bunch of related projects in 2012 were the starting point.

    - Number of manuscripts and images involved increases steadily; exponentially--hundreds of thousands of images added constantly.

    - The question now is--how do we treat such a large set of materials.

- Every manuscript is unique, of course.

- Comparison between the Ellesmere Chaucer and the Hengwrt Chaucer; today with IIIF it can be done through a single viewer. You can take one MS and the other and put them alongside each other. Putting the two documents next to each other in a virtual space--this is the main purpose of IIIF right now (together with annotation in this context).

- Bringing together different manuscripts:

    - _Handschriftenportal_; this is a national aggregator for German libraries;

    - Italians have just adopted IIIF as a national standard (including the Vatican library);

    - _Biblissima_ aggregates French manuscripts.

- Aggregation has been happening in North America as well, since American institutions usually have relatively small collections.

    - OCLC is an attempt in this direction.

- 80,000 MSs in the Vatican; they are--apparently--very poorly catalogued (people do not know what is in there).

    - For this reason, the implementation of IIIF can help us figure out what is in there.

- IIIF is often used to bring together scattered MSs; create a virtual collation that allows one to consult the object as it had been originally produced (with pieces scattered in different places); _reconstructing scattered/dispersed objects_.

- Jeff Witt; he is on the forefront on this kind of work--he has worked on Peter Lombard's sentences.

    - He has used IIIF to build an interaction between libraries and scholars who know the materials better than the libraries themselves.

    - Collaborative annotations among specialists, helping the hosting libraries.

- IIIF "fuels collaboration."

- _Biblissima_ has been _harvesting metadata_ to construct a comprehensive catalogue of annotations (should look into it further).

- _Fragmentarium_ is also designed for aggregation and cataloguing; its purpose is to bringing pieces of MSs back together again.

    - It is designed for _fragmentary objects_.

    - 30,000 individual leaves are scattered throughout the United States (they have been disassembled and sold individually for greedy purposes).

- IIIF has also been used in conjunction with other technologies--especially machine learning:

    - _eScripta_;

    - _Transcribus_;

    - _Himanis_.

        - _Machine learning_ has also been used for feature recognition; one can train a machine to recognize specific kinds of illuminated initials, for instance.

- IIIF has also been used for games; check out the ["slide puzzle"](http://blalbrit.github.io/2016-05-24-slide_puzzle.html) developed by Benjamin Albritton, for instance.

- IIIF is a community; there exist "community groups" that try to meet often--virtually and in person. Here is their dedicated [home page](https://iiif.io/community/groups/manuscripts/).

#### Lisa Fagin Davis: What IIIF means in short

- **IIIF** means: on-line; open access; interoperable.

    - On-line seems self-explanatory.

    - Open access means that it can be downloaded and used in any possible way; through IIIF, it can also be _mirrored_ through its _stable URL_--IIIF comparison works through mirroring: the image lives on one space, and it is then mirrored by every individual online application or implementation.

        - The original file and the persistent URL never change; but they can be mirrored by numberless institutions.

    - This mirroring is what allows for interoperability.

#### Mike Appleby - APIs: What are these?

- Application Programming Interfaces; they allow pieces of software to work together--to be assembled into larger pieces of software.

    - Also known as _Agreements Preceding Interaction_.

- IIIF APIs concern:

    - Images; what they should look like;

    - Presentation; how they should be displayed;

    - Search; allows one to search through plain text (annotations, OCR transcriptions);

    - Authorization; who can use what and how.

##### Image API

1. First thing it defines is a __persistent URL__ associated with the image.

2. It also specifies that an image information document (_info.json_) should be connected to the image itself.

    - A _.json_ document is a machine-readable and human-readable document that contains metadata and specifications of various kinds.

##### Transformation API

1. This specifies what kinds of transformations the image can undergo:

    1. region (the portion of the image that I intend to look at);
    2. size (how big I want the image to be; how many pixels should the image contain);
    3. rotation;
    4. quality;
    5. format.

- So, for instance, through the transformation API I can extract a piece of image ad use it elsewhere; check out this [interactive web page](https://jbhoward-dublin.github.io/IIIF-imageManipulation/index.html?imageID=https://images.britishart.yale.edu/iiif/2/bf9aaac2-5628-4db0-bf94-f55a2e82c541) to see how it works.

    - In practice, if I add more specifications after the URL associated with the image, I will see only a portion of the image itself; the __server__ performs the transformation for me.

    - [Original image](https://images.britishart.yale.edu/iiif/2/bf9aaac2-5628-4db0-bf94-f55a2e82c541).

    - [Modified image](https://images.britishart.yale.edu/iiif/2/bf9aaac2-5628-4db0-bf94-f55a2e82c541/4152,2453,2041,1761/1280,/0/color.tif).

    - https://images.britishart.yale.edu/iiif/2/bf9aaac2-5628-4db0-bf94-f55a2e82c541/4152,2453,2041,1761/1280,/90/gray.tif

        - The first bit after the image URL clarifies the region that I am interested in (the pixels probably refer to the four corners of the box).

        - The second bit specifies the size of the image in pixels (here it is 1280,).

        - The third bit specifies by how much it should be rotated (for instance, by 90 degrees).

        - The fourth bit specifies the quality of the image (color, or gray, or bitonal).

![alt text](https://images.britishart.yale.edu/iiif/2/bf9aaac2-5628-4db0-bf94-f55a2e82c541/4152,2453,2041,1761/1280,/90/gray.tif "Here is what the modified image will look like.")

- Associated to the image itself, one finds an "info.json" file that contains all the techincal information belonging to the image.

    - Image API version;
    - Image API compliance level;
    - Height and width;
    - and more...

##### Presentation API

- The core element is the __IIIF Manifest__; this it the file that contains information concerning how the image should be displayed.

- The interface of IIIF--_Mirador_--loads the Manifest IIIF to display:

    - the _Label_ associated with the image;

    - the _Canvas_, which is the image that is being shown right at a moment

        - (note that the image is selected and displayed thanks to __annotations__; there are of course guidelines concerning these annotations; and annotations generally associate a __body__ with a __target__; in this case the body is the image file, the target is the canvas);

    - _Sequences_ and _Ranges_.

- The Canvas is an element in the .json file; it contains a specification concerning its size (which is a set of coordinates, but not necessarily in pixels).

- The Annotation is a different element; again, it contains coordinates and a "motivation" (the "motivation" would be a clarification concerning why an annotation is being added, or to what element).

- So, the _Canvas_ is a portion--or a display--of a pre-existent image; this _Canvas_ can then be annotated: within the Canvas I clarify the coordinates of the annotation which I intend to add, and the size of the annotation box.

    - The coordinates are disconnected from the pixels because of the _canvas_ layer; note that a __Canvas__ can contain __multiple images__ (so, the annotations are tied to the Canvas, I can display different images and the annotations remain there, anchored to the coordinates of the Canvas itself).

    - _Every image that I see in Mirador, on the Canvas, is an annotation._

        - Annotations and images can overlap; the Canvas contains a __z__ dimension that explains how the images should be piled onto each other.

- __SEQUENCES__ are _lists of Canvases_; every Manifest document contains _at least_ a Canvas and _at least_ a Sequence; the Sequence clarifies the order in which Canvases should we displayed.

    - Canvases can also be ordered in __ranges__; ranges can include canvases and other ranges within them.

    - Sequences are actually disappearing, and being replaced by ranges.

##### Search API

- It allows users to search _within an IIIF object_. The Search engine returns annotations.

##### Authentication API

- This specifies how to redirect users to a Login page, in case some of the content that is being uploaded through IIIF has limited access.

#### Lisa Fagin Davis: IIIF in the wild

- **Reconstructing the Beauvais Missal**. This is an _Omeka_ website that contains the reconstruction of this missal; the missal has been assembled on an [IIIF manifest](http://brokenbooks.org/brokenBooks/getManifest.html?LFD) on _Broken Books_.

- How does one find IIIF Images and Manuscripts?

    - Use the [aggregator prepared by Biblissima](https://iiif.biblissima.fr/collections/).

- __OCLC__ is a colossal aggregator for digitized materials hosted by North American libraries; it contains [many collections](https://researchworks.oclc.org/iiif-explorer/).

- Other lists include: [IIIF Awesome](https://github.com/IIIF/awesome-iiif).

- How does one learn about _best practices_ to handle metadata and coding a IIIF manifest?

    - Look, for instance, at [Parker on the Web](https://parker.stanford.edu/parker/catalog/qd527zm3425); this is so well written that I can drag and drop the _IIIF_ icon and put it in mirador--without copy-pasting anything.

    - Or at [ECodices](https://www.e-codices.unifr.ch/en/searchresult/list/one/csg/0002).

- Other interesting websites: _Fragmentarium_ [link](https://fragmentarium.ms/overview/F-c4kh). Fragmentarium allows one to upload images on the site; once uploaded, the image acquires a IIIF manifest. Eventually, the images can be strung together to form a single coherent manuscript.

    - [Stony Brook University](https://exhibits.library.stonybrook.edu/oem/items/show/483#?c=0&amp;m=0&amp;s=0&amp;cv=0); all their materials have been made IIIF compliant.

    - [Harvard Digital Collections](https://exhibits.library.stonybrook.edu/oem/items/show/483#?c=0&amp;m=0&amp;s=0&amp;cv=0).

- Poor examples:

    - [Gallica](http://api.bnf.fr/api-iiif-de-recuperation-des-images-de-gallica) hides its IIIF button; one needs to know how to create an IIIF manifest from the persistent URL associated with the image.

    - [Digital Commonwealth](https://www.digitalcommonwealth.org/search/commonwealth:7d279x48j) also hides the instructions.

- So, one has the image, with a persistent URL; the image has an _info.json_ associated with it; multiple images are then strung together in a _Manifest_-- which has a _manifest.json_ file associated with it. _Mirador_ requires a _manifest.json_.

## Session 2

### What a Mirador Is

- Play around with the [demo](https://projectmirador.org/demo/).

- It is possible to incorporate the logo of the hosting institution into the meta data associated with an image.

### Using Your Own Images

- Upload them on **archive.org**; through **archivelab.org** one can automatically create a `manifest.json` file. The formula to follow is this:

> `http://iiif.archivelab.org/iiif/IMAGE PATH/manifest.json`

- You can also create your own manifest by using a manifest editor:

    1. [Digirati Manifest Editor](https://iiif-manifest-editor-live-demo.netlify.com/);

    2. [Oxford Manifest Editor](http://iiif.bodleian.ox.ac.uk/manifest-editor).

- You can also run a server from your own computer, using Docker.

---

### Session 2

#### Benjamin Albritton: Telling a Story With Mirador

- We placed different manifests onto our Mirador; remember the steps involved:

    1. adding the address of the manifest.json that matters to us to the list of "data" items;
    2.

- Now, to understand what ...

    - An annotation within IIIF corresponds to a "Linked data construct"; it is a connection between two pieces of information; an annotation is a relationship.

    - __Region of interest__ and __text__.
