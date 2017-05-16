# ABNF Representation

Syntax for a vObject path is defined by the following ABNF notation.

TODO: Probably better to use fragment-unreserved as delimiters.


{align=left}
~~~ abnf
fragment-unreserved = “:" / "@" / "?" / "!" / "$" / "&" /
                      "’" / "(" / ")" / "," / ";" / "=“
                      ; only for authoring development reference

root-delim  = "/"
comp-delim  = "/"
prop-delim  = "&"
param-delim = ";"

comp-name   = text
prop-name   = text
param-name  = text

operator-equal = "="
operator-not-equal = "!="
operator-not-present = "!"
operator-equality = operator-equal / operator-not-equal

vpath = path-absolute / path-relative
  ; generic vPath refers to any component, property or parameter

path-absolute = root-delim comp-segment [prop-path]
  ; a path relative to the root of the vObject

path-relative = *( comp-segment ) [prop-path] / prop-path
  ; a path relative to the position of the "current" component
  ; (empty comp-segment refers to the current component)

prop-path = 1*( prop-segment ) [ *( param-segment ) ]

comp-segment = comp-delim comp-name *( prop-delim prop-match )
  ; a path segment with optional match criteria to select a specific
  ; component with the given name (or object class)

prop-match = prop-presence-match / prop-name prop-value-match

prop-presence-match = [ operator-not-present ] prop-name
  ; matches if the property with the given name is present
  ; (or absent with "!") in the selected component

prop-value-match = operator-equality value-escaped
  ; matches if a component has a property with the given name
  ; and a matching value (using the given operator)


prop-segment = prop-delim prop-name [prop-value-match]
                 *( param-delim param-match )

param-match = param-presence-match / param-name param-value-match
  ; matches a specific property parameter

param-presence-match = [ operator-not-present ] param-name
  ; matches if a specific property parameter is present
  ; (or absent ("!"))

param-value-match = operator-equality value-escaped
  ; matches a specific property parameter and its value


param-segment = param-delim param-name


value-escaped = *( unreserved / pct-encoded )
  ; the escaped value containing only unreserved or percent-encoded
  ; chars

pct-encoded = "%" HEXDIG HEXDIG
  ; taken from RFC 3986

unreserved  = ALPHA / DIGIT / "-" / "." / "_" / "~"
  ; taken from RFC 3986
~~~


