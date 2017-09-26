#  Introduction {#introduction}

It is often necessary to refer to a particular element within a
vObject, for example, in the case of patching a vObject component
[@VPATCH] with differential updates. Here we define a mechanism called
"vObject Path", to describe an element's location within a vObject.

For example, the "REL" property in a vCard Profile component contains a
vCard Property Path, which is used to match a property within the vCard
to indicate the profile's linkage on this property.

This specification was developed as joint work between TC Calendar
[@CALCONNECT-CALENDAR] and TC VCARD [@CALCONNECT-VCARD] committees at
CalConnect, the Calendaring and Scheduling Consortium.

## vPath Within a vObject

vPath syntax allows a value within a vObject to refer to other
vObject(s) or element(s) within an enclosing vObject or an underlying
vObject.

TODO elaborate.

## vPath Within Fragments

The vPath syntax is designed to be "fragment-friendly" adhering to the
URI fragment syntax defined in [@RFC3986].

This document defines URI fragment identifiers for both the "text/vcard"
[@RFC6350] and "text/calendar" [@RFC5545] media types.

This makes it possible to utilize the vPath to refer to an element of a
vObject that can be located through a URI [@RFC3986].

## vPath For Queries

TODO: e.g., in CardQL vPath is used to search and filter results of
vCards / Address Books.
