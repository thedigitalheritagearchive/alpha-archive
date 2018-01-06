# The Digital Heritage Archive

This archive is an attempt to collate all material relating to the preservation of hardware and software in the retro computing arena.

# IMPORTANT ALPHA RELEASE NOTICE
## The structure of this data is in flux. The content is incomplete. Everything here is presented as a request for comments, to help solidify the ideas and requirements before the structure is created for real - we don't want to waste too much time!


## Background

This archive is not intending to replace any of the existing web sites on retro computing, of which there are many, but supplement them by providing a means of discovery and a structured model in which to present, preserve, and cross-reference information - not just from one site, but all of them. In most cases, each asset (e.g. software, manual, etc) will be linked from here to third party sites, with this archive holding only the metadata.

## Questions for the community

* Is this is worthwhile project?
* Does it add anything, beyond a list of links to the existing websites?
* Is the structure of each XML file sensible? Useful?


## Items

Everything that exists in the computer universe is called an 'item'. Each items has a 'type', which includes companies, people, computers, peripherals, software, manuals, magazines, and so on. Each item is described using an identical structure, beginning in the same way:

```
<heritage-company>
	<item name="Company name Ltd" type="company"  id="" content="">
		<abstract>A one line comment about the item. Factual.</abstract>
		<editorial>A longer piece of information about the item. Factual.</editorial>
		<references>
			<xref href="http://something_or_other" format="html" scope="external">A third party site, or page, that covers the item fully.</xref>
		</references>
		<commentary>Information that demonstrates how this item fits into the broad context of computing. May be opinion-based.</commentary>
		<note>
			<opinion individual_id="">Some personal thoughts/stories that are relevant to the heritage of the item.</opinion>
		</note>

		<!-- item type specifics go here -->
	</item>
</heritage-company>
```

Each _type_ has it's own "heritage-" element name. Current names include: company, individual, product, manual, doc, image, and schematic.

The ID is an MD5 checksum, unique to each item. It can be computed from anything, but conventionally we've used the item type and name. Everything will eventually, I hope, be cross-linked and referenced by means of these unique IDs, present with each item. The long term hope is that these become _THE_ IDs by which all computing items are refered, like the IDs on an IMDB page for film.

The CONTENT is an MD5 checksum of the attached data file, if appropriate.

After these common elements, the type-specific elements are included. There are examples in the archive.

## Purpose

From a hardware perspective, we want to hold enough information to help people repair their machines by detailing the schematics, components, and thoughts from preservation experts around the world. This will include alternative product parts, tolerances, schematic diagrams and other useful information

The software archives will detail the people behind the products, so individual careers can be traced - even between different machines. It is on this latter point where I hope the archive has value.

There is scope in the format for individuals to add personal comments and stories, since these are the lifeblood of computing. It also allows them to add serial numbers of the machines they personally own, to maintain provenance. It might be useful for tracking thefts and dishonest ebay sellers; it might be useful for tracing machines belonging to famous users; or it might be useless!

An interesting addition is the _xref_ type. This holds links and software to cross-platform development tools, like emulators and cross-compilers, that allow a future generation to truly understand and build software for these old machines.

## Basic folder structure

Each item is stored under a folder structure in the form:

```
company / product / SKU
```

This directory structure is a convention only, to make finding machines easier.

There are no rules about how big or small a company is to warrant inclusion, although only the direct production company is referenced by the directory name; ownership is stored in the accompanying metadata. As an example, if company X owned company Y, and it was company Y that made a computer, then the directory would be Y with X & Y being detailed in XML.

Also, a company can be any producer of content: a hardware manufacturer, magazine publisher, or software developer. Each type of company dictates both the format of its metadata and the meaning of the subdirectory called 'product'. In the case of a computer manufacturer, 'product' means 'computer name', while in the case of a publisher 'product' would mean 'magazine title'.

SKU is short for 'stock keeping unit', and is the specific version of that product. This might be issue 3 of the 48K version of the ZX Spectrum, or the 1984 Christmas issue of the Sinclair User magazine.

Within each SKU folder is all the collated data about that specific item. This depends on the type of item. It might include original materials such as schematics and manuals, along with third party content such as photographs, emulators, and cross-platform development tools.


## A typical project item

Taking a standard Dragon 32 as an example, here's how the various XML files are organised.

* contrib - for third-party miscellaneous information about the specific machine, which wasn't available or produced at the time of manufacture/sale
* docs - official documentation from the manufacturer that wasn't sold as a publication in its own right. e.g. errata sheets
* firmware - ROM images and the like
* images - pictures of the product, either official or independent. The XML file for each image gives details
* manuals - as supplied with the machine
* schematics - images, PDFs, and/or text descriptions of the product. Includes circuits, service manual, technical specs, and so on
* xdev - Cross-platform development tools, like emulators, assemblers, and compilers


## Notes

* We have an ID for each named person, and a textual form. This might appear duplication (and therefore bad form) but it is because of two reasons:
  1. It is easier to process documents, since one has all the information locally. This is historical data after all, so it doesn't change.
  2. If names are misprinted that error is preserved, but the link to the person matches their other credits.


