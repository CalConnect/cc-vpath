# Path Types

A vObject path can either be an "absolute" or "relative" path.


## Absolute Path

An absolute vObject path:

* Always starts with "/".
* The frame of reference begins at the top-level vObject.
* Refers to an element under the hierarchy of the top-level vObject.

An absolute path always starts with a "/" followed by a component
segment (the vObject name), as only vObjects are allowed at the top most
vObject level.

Example:

* `//VCARD#TEL`: refers to the `TEL` properties of the top-level `VCARD`
  components


## Relative Path

* Does not start with "/".
* The frame of reference begins at the current level vObject.
* Refers to an element under the hierarchy of the current level vObject.

A relative path can start with a component segment or a property
segment, with the path assumed to be relative to an enclosing
component defined by the context.

* `/VEVENT#UID`: refers to the `UID` properties of the current level
  `VEVENT` components.


Relative paths are unable to refer to an element that is outside of the
current component. The only way to do so is through an absolute path.
This restriction is for simplicity and to address security concerns,
while conforming in expectation to the usage of XPath [@!RFC5261].


