# Simple Item Page

## Introduction

This page describes the customizations made to the MD-SOAR "simple" item
page display.

## Simple Item Page Layout

### Left sidebar

* Thumbnail/Files
  * `<From DSpace object>`
* Files
  * `<Links to all files in DSpace object>`
* Permanent Link
  * dc.identifier.uri
* Collections
  * `<From DSpace>`
* Metadata
  * `<Link to “full item record” page>`
  * **Note:** DSpace 7 provides a "Full item page" button, which is used in
    place of the "Metadata" label and link.

### Center of Page

* Author/Creator
  * dc.contributor.author
* Author/Creator ORCID
  * dc.creator
* Date
  * dc.date
  * dc.date.issued
  * dc.date.created
  * dc.date.copyright
  * dctermscreated
  * dctermsdate
  * dcterms.dateAccepted
  * dcterms.dateCopyrighted
* Type of Work
  * dc.genre
  * dc.type
  * dc.format
  * dcterms.format
* Department
  * dc.contributor.department
* Program
  * dc.contributor.program
* Citation of Original Publication
  * dc.identifier.citation
  * dcterms.bibiographicCitation
* Rights
  * dc.rights
  * dcterms.accessRights
* Subjects
  * dc.subject
  * dc.subject.lcsh
  * dc.subject.mesh
  * dc.coverage.temporal
  * dc.coverage.spatial
* Abstract
  * dc.description.abstract

## Field Value Hyperlinks

The following fields display their values with hyperlinks:

* Files
* Permanent Link
* Collections
* Author/Creator
* Date
  * Any "date
* Type of Work - See note
* Subjects

**Note:** The "Date" and "Type of Work" field values were *not* hyperlinked in
DSpace 6.

The hyperlinks (and which index they connect to) is controlled by the
"webui.browse.link.\<n>" entries in the "dspace/config/local.cfg" file.

The each "webui.browse.link" entry must specify an existing index in the
"webui.browse.index" list to link to.
