# Path Segments

The vObject Path is composed of a list of "segments" that matches an
vObject element in the vObject object model hierarchy.

Segments are separated by segment prefixes within the vObject Path.
Depending on the element type described, a path segment is always
preceded by the following prefix ("path segment prefix"):

Valid prefixes are as follows:

* Component: "/"
* Property: "@"
* Property parameter: ";"
* Property value: "="
* Property parameter value: "="

A path can start with a series of component segments (which always
have a "/" prefix).  Those can be followed by a property segment
(which always has a "@" prefix").  A property segment can be followed
by either a parameter segment (which always has a ";" prefix), or a
value segment (which always has a "=" prefix).  A parameter segment
can be followed by a value segment (which always has a "=" prefix).


## Encoding

TODO.


## Character Set

TODO. Both vCard [@RFC6350] and iCalendar [@RFC5545] use UTF-8
[@RFC3629].


<!--
From RFC 2854 Section 6

The use of an explicit charset parameter is strongly recommended.
While [MIME] specifies "The default character set, which must be
assumed in the absence of a charset parameter, is US-ASCII."  [HTTP]
Section 3.7.1, defines that "media subtypes of the 'text' type are
defined to have a default charset value of 'ISO-8859-1'".  Section
19.3 of [HTTP] gives additional guidelines.  Using an explicit
charset parameter will help avoid confusion.

Using an explicit charset parameter also takes into account that the
overwhelming majority of deployed browsers are set to use something
else than 'ISO-8859-1' as the default; the actual default is either a
corporate character encoding or character encodings widely deployed
in a certain national or regional community. For further
considerations, please also see Section 5.2 of [HTML40].
-->
