# XPath/XSLT functions

In addition to the standard XPath/XSLT functions (see [W3Schools](https://www.w3schools.com/xml/xsl_functions.asp)), eMagiz also supports the functions that are listed below. These extension functions are located in following namespaces:
- `"http://www.emagiz.com/ns/mapping/1.0/"` for the mapping functions (prefixed with `mapping` in this document)  
- `"http://www.emagiz.com/ns/xml/1.0/"` for generic eMagiz extension functions (prefixed with `ezx` in this document)

## lookup-cdm-code
```xquery
string mapping:lookup-cdm-code(string system, string codeType, string systemCode, boolean mustExist)
```
Looks up the CDM code for the given system code. If caching is enabled, the CDM code will be returned from the cache if possible, otherwise it will be added to the cache after performing the lookup so subsequent calls can use this cached value.

#### Parameters:
- **system** identifier of the system to do the lookup for (not null or empty, max length 64)  
- **codeType** type of code to do the lookup for (not null or empty, max length 64)  
- **systemCode** system code to do the lookup for (not null or empty, max length 64)  
- **mustExist** if true, a MappingException is thrown when the resulting CDM code would be null or empty  

#### Returns:
the requested CDM code (if mustExist is false, the value might be null or empty, indicating no code element was present in the mapping service response or the code element was present but didn't have a value)

## lookup-system-code
```xquery
string mapping:lookup-system-code(string system, string codeType, string cdmCode, boolean mustExist)
```
Looks up the system code for the given CDM code. If caching is enabled, the system code will be returned from the cache if possible, otherwise it will be added to the cache after performing the lookup so subsequent calls can use this cached value.

#### Parameters:
- **system** identifier of the system to do the lookup for (not null or empty, max length 64)
- **codeType** type of code to do the lookup for (not null or empty, max length 64)
- **cdmCode** CDM code to do the lookup for (not null or empty, max length 64)
- **mustExist** if true, a MappingException is thrown when the resulting system code would be null or empty

#### Returns:
the requested system code (if mustExist is false, the value might be null or empty, indicating no code element was present in the mapping service response or the code element was present but didn't have a value)

## lookup-custom-attribute
```xquery
string mapping:lookup-custom-attribute(string codeType, string cdmCode, string customAttribute, boolean mustExist)
```
Looks up the value for the specified custom attribute of the given CDM code. If caching is enabled, the custom attribute value will be returned from the cache if possible, otherwise it will be added to the cache after performing the lookup so subsequent calls can use this cached value.

#### Parameters:
- **codeType** type of code to do the lookup for (not null or empty, max length 64)  
- **cdmCode** CDM code to do the lookup for (not null or empty, max length 64)  
- **customAttribute** custom attribute to do the lookup for (not null or empty, max length 64)  
- **mustExist** if true, a MappingException is thrown when the resulting custom attribute value would be null or empty  

#### Returns:
the value of the requested custom attribute (if mustExist is false, the value might be null or empty, indicating no value element was present in the mapping service response or the value element was present but didn't have a value)

## format-dateTime
```query
string ezx:format-dateTime(dateTime dateTime, string pattern)

string ezx:format-dateTime(dateTime dateTime, string pattern, string timeZone)
```
Formats a given date/time as a string using the specified pattern.

#### Parameters:
- **dateTime** the date/time to format  
- **pattern** the pattern (a string following the DateTimeFormat pattern syntax) to use for formatting the date/time   
- **timeZone** [Optional] the time zone (a string as accepted by DateTimeZone.forID(String)) to use when formatting the output; if not specified the time zone of the input date/time is used (which, when unspecified, defaults to UTC if the input is an instance of xs:dateTime or the JVM local time zone otherwise)  

#### Returns:
The formatted date/time as a string value.

#### Example:
`ezx:format-dateTime('2014-01-01T04:45:30.000+01:00', 'E MMM dd yyyy h:mma Z')`

*Result:* `Wed Jan 01 2014 4:45AM +0100`

#### Example:
`ezx:format-dateTime('2014-01-01T04:45:30.000+01:00', 'E MMM dd yyyy h:mma Z', 'America/New_York')`

*Result:* `Tue Dec 31 2013 10:45PM -0500`

## format-date
```query
string ezx:format-date(date date, string pattern)

string ezx:format-date(date date, string pattern, string timeZone)
```
Formats a given date as a string using the specified pattern.

#### Parameters:
- **date** the date to format  
- **pattern** the pattern (a string following the DateTimeFormat pattern syntax) to use for formatting the date   
- **timeZone** [Optional] the time zone (a string as accepted by DateTimeZone.forID(String)) to use when formatting the output; if not specified the time zone of the input date is used (which, when unspecified, defaults to UTC if the input is an instance of xs:date or the JVM local time zone otherwise)  

#### Returns:
The formatted date as a string value.

#### Example:
`ezx:format-date('2014-01-01+01:00', 'E MMM dd yyyy Z')`

*Result:* `Wed Jan 01 2014 +0100`

#### Example:
`ezx:format-date('2014-01-01+01:00', 'E MMM dd yyyy Z', 'America/New_York')`

*Result:* `Tue Dec 31 2013 -0500`

## format-time
```xquery
string ezx:format-time(time time, string pattern)

string ezx:format-time(time time, string pattern, string timeZone)
```
Formats a given time as a string using the specified pattern.

#### Parameters:
- **time** the time to format  
- **pattern** the pattern (a string following the DateTimeFormat pattern syntax) to use for formatting the time  
- **timeZone** [Optional] the time zone (a string as accepted by DateTimeZone.forID(String)) to use when formatting the output; if not specified the time zone of the input time is used (which, when unspecified, defaults to UTC if the input is an instance of xs:time or the JVM local time zone otherwise)  

#### Returns:
The formatted time as a string value.

#### Example:
`ezx:format-time('04:45:30.000+01:00', 'h:mma Z')`

*Result:* `4:45AM +0100`

#### Example:
`ezx:format-time('04:45:30.000+01:00', 'h:mma Z', 'America/New_York')`

*Result:* `10:45PM -0500`

## parse-dateTime
```xquery
dateTime ezx:parse-dateTime(string stringValue, string pattern)

dateTime ezx:parse-dateTime(string stringValue, string pattern, string timeZone)
```
Parses a given string value into a date/time using the specified pattern.

#### Parameters:
- **stringValue** the string value to parse into a date/time   
- **pattern** the pattern (a string following the DateTimeFormat pattern syntax) to use for parsing the string value into a date/time  
- **timeZone** [Optional] the time zone (a string as accepted by DateTimeZone.forID(String)) to use when parsing the input, completely ignoring any time zone information in the string value; if not specified the time zone information in the string value is used (which, when not present, defaults to the JVM local time zone)  

#### Returns:
The parsed date/time as a dateTime value.

#### Example:
`ezx:parse-dateTime('Wed Jan 01 2014 4:45AM +0100', 'E MMM dd yyyy h:mma Z')`

*Result:* `2014-01-01T04:45:00+01:00`

#### Example:
`ezx:parse-dateTime('Wed Jan 01 2014 4:45AM +0100', 'E MMM dd yyyy h:mma Z', 'America/New_York')`

*Result:* `2014-01-01T04:45:00-05:00`

## parse-date
```xquery
date ezx:parse-date(string stringValue, string pattern)

date ezx:parse-date(string stringValue, string pattern, string timeZone)
```
Parses a given string value into a date using the specified pattern.

#### Parameters:
- **stringValue** the string value to parse into a date   
- **pattern** the pattern (a string following the DateTimeFormat pattern syntax) to use for parsing the string value into a date  
- **timeZone** [Optional] the time zone (a string as accepted by DateTimeZone.forID(String)) to use when parsing the input, completely ignoring any time zone information in the string value; if not specified the time zone information in the string value is used (which, when not present, defaults to the JVM local time zone)  

#### Returns:
The parsed date as a date value.

#### Example:
`ezx:parse-date('Wed Jan 01 2014 +0100', 'E MMM dd yyyy Z')`

*Result:* `2014-01-01+01:00`

#### Example:
`ezx:parse-date('Wed Jan 01 2014 +0100', 'E MMM dd yyyy Z', 'America/New_York')`

*Result:* `2014-01-01-05:00`

## parse-time
```xquery
time ezx:parse-time(string stringValue, string pattern)

time ezx:parse-time(string stringValue, string pattern, string timeZone)
```
Parses a given string value into a time using the specified pattern.

#### Parameters:
- **stringValue** the string value to parse into a time   
- **pattern** the pattern (a string following the DateTimeFormat pattern syntax) to use for parsing the string value into a time  
- **timeZone** [Optional] the time zone (a string as accepted by DateTimeZone.forID(String)) to use when parsing the input, completely ignoring any time zone information in the string value; if not specified the time zone information in the string value is used (which, when not present, defaults to the JVM local time zone)  

#### Returns:
The parsed time as a time value.

#### Example:
`ezx:parse-time('4:45AM +0100', 'h:mma Z')`

*Result:* `04:45:00+01:00`

#### Example:
`ezx:parse-time('4:45AM +0100', 'h:mma Z', 'America/New_York')`

*Result:* `04:45:00-05:00`

## remove-timezone-from-dateTime
```xquery
dateTime ezx:remove-timezone-from-dateTime(dateTime dateTime)
```
Removes all timezone information from the given date/time without changing its value.

#### Parameters:
- **dateTime** the date/time to remove the timezone information from

#### Returns:
The date/time without any timezone information as a dateTime value.

#### Example:
`ezx:remove-timezone-from-dateTime('2014-01-01T04:45:30.000+01:00')`

*Result:* `2014-01-01T04:45:30`

## remove-timezone-from-date
```xquery
date ezx:remove-timezone-from-date(date date)
```
Removes all timezone information from the given date without changing its value.

#### Parameters:
- **date** the date to remove the timezone information from

#### Returns:
The date without any timezone information as a date value.

#### Example:
`ezx:remove-timezone-from-date('2014-01-01+01:00')`

*Result:* `2014-01-01`

## remove-timezone-from-time
```xquery
time ezx:remove-timezone-from-time(time time)
```
Removes all timezone information from the given time without changing its value.

#### Parameters:
- **time** the time to remove the timezone information from

#### Returns:
The time without any timezone information as a time value.

#### Example:
`ezx:remove-timezone-from-time('04:45:30.000+01:00')`

*Result:* `04:45:30`

## adjust-dateTime-to-timezone
```xquery
dateTime ezx:adjust-dateTime-to-timezone(dateTime dateTime, string timeZone)
```
Adjusts the given date/time to the specified timezone (respecting the original timezone).

#### Parameters:
- **dateTime** the date/time to adjust to a timezone; when the timezone of this date/time is unspecified, it defaults to UTC if the input is an instance of xs:dateTime or the JVM local time zone otherwise   
- **timeZone** the time zone (a string as accepted by DateTimeZone.forID(String)) to adjust the date/time to  

#### Returns:
The adjusted date/time as a dateTime value.

#### Example:
`ezx:adjust-dateTime-to-timezone('2014-01-01T04:45:30.000+01:00', 'America/New_York')`

*Result:* `2013-12-31T22:45:30-05:00`

## adjust-date-to-timezone
```xquery
date ezx:adjust-date-to-timezone(date date, string timeZone)
```
Adjusts the given date to the specified timezone (respecting the original timezone).

#### Parameters:
- **date** the date to adjust to a timezone; when the timezone of this date is unspecified, it defaults to UTC if the input is an instance of xs:date or the JVM local time zone otherwise   
- **timeZone** the time zone (a string as accepted by DateTimeZone.forID(String)) to adjust the date to  

#### Returns:
The adjusted date as a date value.

#### Example:
`ezx:adjust-date-to-timezone('2014-01-01+01:00', 'America/New_York')`

*Result:* `2013-12-31-05:00`

## adjust-time-to-timezone
```xquery
time ezx:adjust-time-to-timezone(time time, string timeZone)
```
Adjusts the given time to the specified timezone (respecting the original timezone).

#### Parameters:
- **time** the time to adjust to a timezone; when the timezone of this time is unspecified, it defaults to UTC if the input is an instance of xs:time or the JVM local time zone otherwise   
- **timeZone** the time zone (a string as accepted by DateTimeZone.forID(String)) to adjust the time to  

#### Returns:
The adjusted time as a time value.

#### Example:
`ezx:adjust-time-to-timezone('04:45:30.000+01:00', 'America/New_York')`

*Result:* `22:45:30-05:00`

## override-timezone-of-dateTime
```xquery
dateTime ezx:override-timezone-of-dateTime(dateTime dateTime, string timeZone)
```
Overrides the timezone of the given date/time with the specified timezone (ignoring the original timezone).

#### Parameters:
- **dateTime** the date/time to override the timezone of; whether this date/time specifies a timezone or not is irrelevant, as it will be overridden anyway   
- **timeZone** the time zone (a string as accepted by DateTimeZone.forID(String)) to override the date/time with  

#### Returns:
The date/time with the new timezone as a dateTime value.

#### Example:
`ezx:override-timezone-of-dateTime('2014-01-01T04:45:30.000+01:00', 'America/New_York')`

*Result:* `2014-01-01T04:45:30-05:00`

## override-timezone-of-date
```xquery
date ezx:override-timezone-of-date(date date, string timeZone)
```
Overrides the timezone of the given date with the specified timezone (ignoring the original timezone).

#### Parameters:
- **date** the date to override the timezone of; whether this date specifies a timezone or not is irrelevant, as it will be overridden anyway   
- **timeZone** the time zone (a string as accepted by DateTimeZone.forID(String)) to override the date with  

#### Returns:
The date with the new timezone as a date value.

#### Example:
`ezx:override-timezone-of-date('2014-01-01+01:00', 'America/New_York')`

*Result:* `2014-01-01-05:00`

## override-timezone-of-time
```xquery
time ezx:override-timezone-of-time(time time, string timeZone)
```
Overrides the timezone of the given time with the specified timezone (ignoring the original timezone).

#### Parameters:
- **time** the time to override the timezone of; whether this time specifies a timezone or not is irrelevant, as it will be overridden anyway   
- **timeZone** the time zone (a string as accepted by DateTimeZone.forID(String)) to override the time with  

#### Returns:
The time with the new timezone as a time value.

#### Example:
`ezx:override-timezone-of-time('04:45:30.000+01:00', 'America/New_York')`

*Result:* `04:45:30-05:00`

## call-xslt-extension-gateway
```xquery
node ezx:call-xslt-extension-gateway(gateway gateway, node request) 
```
Calls the given XSLT extension gateway and returns the response XML message.

#### Parameters:
- **gateway** the XSLT extension gateway to call (should be passed to the stylesheet as an <xsl:param/> value)  
- **request** the request message (a single XML node) to send to the gateway; this XML node will be serialized into a string value before sending it to the gateway   

#### Returns:
The response message (a single XML node) received from the gateway; the gateway's string response will be parsed as an XML document before it is returned. 

#### Example:
`ezx:call-xslt-extension-gateway($gateway, //Customer[1]) `

*Result:* `<CustomerDetails>...</CustomerDetails>`
