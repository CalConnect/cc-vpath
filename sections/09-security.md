#  Security Considerations

* Security considerations around vObject formats in the following
documents **MUST** be adhered to:

  * vCard: [@!RFC6350]
  * iCalendar: [@!RFC5545], [@!RFC5789], [@!RFC4791]

* A vPath may point to invalid addresses which could lead to confusion,
  depending on the handling of the client application.

* Seeing vPath as fragment identifier **MAY** confuse people such as
  `https://example.com/vcard#//VCARD@TEL` as it is different from the HTML
  fragment that people assume. People may get exploited through such
  misunderstanding in a similar way to spoofing and phishing.

* Software that implement vPath fragment identifiers and those that do
  not, differ in behavior. The fact that these two types of software
  present differently given the same vPath fragment **MAY** cause confusion
  between users.

* Implementers and users of vObject fragment identifiers **SHOULD**
take into account of security considerations provided in
Section 7 of [@!RFC3986] and Section 8 of [@!RFC3987].

<!-- Adapted from RFC 5147 -->

* Please note that fragment identifiers are only used after the URI resource
  is retrieved, not when resolving the URI for retrieving the resource.
