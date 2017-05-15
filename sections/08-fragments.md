# Fragment Identifier

TODO: below lifted from RFC 2854, reword this.

The URI specification [@RFC3986] notes that the semantics of a fragment
identifier (part of a URI after a "#") is a property of the data
resulting from a retrieval action, and that the format and
interpretation of fragment identifiers is dependent on the media type of
the retrieval result.

For documents of the text/vcard and text/calendar media types, the
fragment specifies the desired vPath of the document.

## Character Set

TODO. Fragments are in US-ASCII charset. UTF-8 content (such as
    for matching) should be encoded in the method of [@RFC3986])

% RFC 3986 Section 2.5
%
% For most systems, an unreserved character appearing within a URI
% component is interpreted as representing the data octet corresponding
% to that character's encoding in US-ASCII.  Consumers of URIs assume
% that the letter "X" corresponds to the octet "01011000", and even
% when that assumption is incorrect, there is no harm in making it.  A
% system that internally provides identifiers in the form of a
% different character encoding, such as EBCDIC, will generally perform
% character translation of textual identifiers to UTF-8 [STD63] (or
% some other superset of the US-ASCII character encoding) at an
% internal interface, thereby providing more meaningful identifiers
% than those resulting from simply percent-encoding the original
% octets.
%
% For example, consider an information service that provides data,
% stored locally using an EBCDIC-based file system, to clients on the
% Internet through an HTTP server.  When an author creates a file with
% the name "Laguna Beach" on that file system, the "http" URI
% corresponding to that resource is expected to contain the meaningful
% string "Laguna%20Beach".  If, however, that server produces URIs by
% using an overly simplistic raw octet mapping, then the result would
% be a URI containing "%D3%81%87%A4%95%81@%C2%85%81%83%88".  An
% internal transcoding interface fixes this problem by transcoding the
% local name to a superset of US-ASCII prior to producing the URI.
% Naturally, proper interpretation of an incoming URI on such an
% interface requires that percent-encoded octets be decoded (e.g.,
% "%20" to SP) before the reverse transcoding is applied to obtain the
% local name.
%
%
