# Targeting and Matching

## Components

To target a second-level component, a component segment is appended to
the path.

Component segments can include an optional match item.  When present,
this allows targeting of components that:

* match existence of (or lack thereof) a property
* match a specific property value
* TODO: match based on property parameters and parameter values

Specific vObjects may define specific matching criteria, for example
in iCalendar Path, the "RID" property matcher can be used to match the
"master" component by the special value of "M" or the general "ridval"
value such as "20160902T223000Z".


## Properties

To target a property inside of a component, a property segment is added
to the path.

A property segment can include an optional match item. When present,
this allows targeting of properties:

* by value (matching or not matching a specific value)
* contains or lack a particular property parameter
* by property parameter value (matching or not matching a specific value)


## Property Parameters

To target a property parameter, a parameter segment is added to the
property segment at the end of the path.

To target a single value in a multi-valued property, a value segment
is added to the property segment at the end of the path.

To target a single value in a multi-valued property parameter, a value
segment is added to the parameter segment at the end of the path.


## Match Syntax

Values in match items **MUST** use URL-style percent ("%") encoding of
the characters "/", "#", ";", "=", and "]".  This allows a path to be
quickly split into segments by breaking apart the text on the relevant
delimiter characters.

TODO: provide ABNF representation

TODO: Singular/plural match, and access to singular plural results.

