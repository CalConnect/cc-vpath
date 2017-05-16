#  Security Considerations

Security considerations around vObject formats in the following
documents **MUST** be adhered to:

* vCard: [@!RFC6350]
* iCalendar: [@!RFC5545], [@!RFC5789], [@!RFC4791]

TODO

* vPath may point to invalid addresses
* vPath as fragment identifier may confuse people such as
`https://a.com/vcard#//VCARD#TEL` as it is different from the HTML
fragment that people assume. People may get exploited through such
misunderstanding in a similar way to spoofing and phishing.

Software that implement vPath fragment identifiers and those that do
not, differ in behavior. The fact that these two types of software
present differently given the same vPath fragment can cause confusion
between users.

Implementers and users of vObject fragment identifiers **SHOULD**
take into account of security considerations provided in [@!RFC3986
Section 7] and [@!RFC3987 Section 8].

<!-- Adapted from RFC 5147 -->

Please note that fragment identifiers are not used when resolving a URI
to retrieve the representation of a resource.

