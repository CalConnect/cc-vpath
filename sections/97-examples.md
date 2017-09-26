# Examples

```
# specify the 3rd card with a tel and point to tel
/VCARD(@tel):first(1):offset(2)@tel
/VCARD(@n:index(0)='Tam' | ;type='home')
/VCARD(@n:index(0)='Tam' | ;type!='home')
/VCARD(!@tel)
/VCARD(@n:index(0)='Tam' | ;type='home')
/VCARD(@n:index(0)='Tam' | ;type:starts-with('h'))
/VCARD(@n:index(0):equals('Tam')
/VCARD(@n:index(0):starts-with('Tam')
/VCARD(@n:index(0):ends-with('Tam')
/VCARD(@n:index(0):contains('Tam')

# has to escape regular expressions like *
/VCARD(@n:index(0):matches(/Ta[nm]/)

/VCARD(@n:index(-1):contains('Tam')


```

## Referring To Components

Path contains exactly one or more component segments:

* `/VCARD`

  Targets the "VCARD" component in the vCard object [@!RFC6350].

* `/VCALENDAR/VEVENT`

  Targets all "VEVENT" components in the "VCALENDAR" component in the
  iCalendar object.

* `/VCALENDAR/VEVENT(@uid='1234')`

  Targets any "VEVENT" components that have a "UID" property value
  exactly equal to "1234", in the "VCALENDAR" component in the iCalendar
  object.

* `/VCALENDAR/VEVENT(@uid='1234%2F4567' & !@recurrence-id)`

  Targets any "VEVENT" components that have a "UID" property value
  exactly equal to "1234/4567" and do not have a "RECURRENCE-ID"
  property, in the "VCALENDAR" component in the iCalendar object.

* `/VCALENDAR/VEVENT(@uid='1234' & @recurrence-id='20160902T223000Z')`

  Targets any "VEVENT" components that have a "UID" property value exactly
  equal to "1234" and have a "RECURRENCE-ID" property whose UTC value is
  "20160902T223000Z", in the "VCALENDAR" component in the iCalendar
  object.


## Referring To Properties

[TODO, lifted from VPATCH]

Path contains exactly zero or more component segments, and one property segment.

* `/VCALENDAR/VEVENT@status`

  Targets all "STATUS" properties in all "VEVENT" components in the
  "VCALENDAR" component in the iCalendar object.

* `/VCALENDAR/VEVENT(@uid='1234')@status`

  Targets all "STATUS" properties in any "VEVENT" components that have a
  "UID" property value exactly equal to "1234", in the "VCALENDAR"
  component in the iCalendar object.

* `/VCALENDAR/VEVENT@ATTENDEE(='mailto:cyrus@example.com')`
  or `/VCALENDAR/VEVENT(@attendee='mailto:cyrus@example.com')@ATTENDEE`

  Targets any "ATTENDEE" properties that have the value
  "mailto:cyrus@example.com" in all  "VEVENT" components, in the
  "VCALENDAR" component in the iCalendar object.

* `/VCALENDAR/VEVENT@ATTENDEE(!='mailto:cyrus@example.com')`

  Targets any "ATTENDEE" properties that do not have the value
  "mailto:cyrus@example.com" in all "VEVENT" components, in the
  "VCALENDAR" component in the iCalendar object.

* `/VCALENDAR/VEVENT@ATTENDEE(;MEMBER)`

  Targets any "ATTENDEE" properties that have a "MEMBER" property
  parameter present in all "VEVENT" components, in the "VCALENDAR"
  component in the iCalendar object

* `/VCALENDAR/VEVENT@ATTENDEE(;cn='Cyrus Daboo')`

  Targets any "ATTENDEE" properties that have a "CN" property parameter
  with the value "Cyrus Daboo" present in all "VEVENT" components, in
  the "VCALENDAR" component in the iCalendar object.

* `/VCALENDAR/VEVENT@ATTENDEE(;cn!='Cyrus Daboo')`

  Targets any "ATTENDEE" properties that have a "CN" property parameter
  not equal to the value "Cyrus Daboo", or do not have a "CN" property
  parameter present in all  "VEVENT" components, in the "VCALENDAR"
  component in the iCalendar object.

* `@ATTENDEE(='mailto:cyrus@example.com')`

  A relative path that targets any "ATTENDEE" properties that have the
  value "mailto:cyrus@example.com" in all components the path is
  relative to.


## Referring To Property Parameters

[TODO, lifted from VPATCH]

Path contains exactly zero or more component segments, one property
segment, and one parameter segment.

* `/VCALENDAR/VEVENT@ATTENDEE;PARTSTAT`

  Targets the "PARTSTAT" parameter on all "ATTENDEE" properties in all
  "VEVENT" components in the "VCALENDAR" component in the iCalendar
  object.

* `/VCALENDAR/VEVENT@ATTENDEE(='mailto:cyrus@example.com');PARTSTAT`

  Targets the "PARTSTAT" parameter on any "ATTENDEE" properties that
  have the value "mailto:cyrus@example.com" in all "VEVENT" components,
  in the "VCALENDAR" component in the iCalendar object.



## Referring To Property Values

[TODO, lifted from VPATCH]

Path contains exactly zero or more component segments, one property
segment, and one value segment.

* `/VCALENDAR/VEVENT@EXDATE(='20160905')`

  Targets all "EXDATE" property values with the value "20160905" in all
  "VEVENT" components in the "VCALENDAR" component in the iCalendar
  object.


## Referring To Property Parameter Values

[TODO, lifted from VPATCH]

Path contains exactly zero or more component segments, one property
segment, one parameter segment, and one value segment.

* `/VCALENDAR/VEVENT@ATTENDEE;MEMBER(='mailto:group@example.com')`

  Targets all "MEMBER" property parameter values with the value
  "mailto:group@example.com" in all "ATTENDEE" properties in all
  "VEVENT" components in the "VCALENDAR" component in the iCalendar
  object.


## Fragment Usage Examples

Plural results:

* `https://example.com/cyrus.vcf#//VCARD@TEL`
* `https://example.com/cyrus/vcard#//VCARD@TEL`
* `https://example.com/cyrus/vcard#//VCARD/PROFILE(1)@TEL;TYPE`

Singular results:

* `https://example.com/cyrus.vcf#//VCARD&TEL(1)`
  * => `"TEL;TYPE=home,work:+123456789"`
* `https://example.com/cyrus/vcard#//VCARD/PROFILE(1)@TEL(1);TYPE`
  * => `"home,work"`
