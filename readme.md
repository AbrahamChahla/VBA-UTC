# VBA-UtcConverter

UTC and ISO 8601 date conversion and parsing for VBA (Windows and Mac Excel, Access, and other Office applications).

Tested in Windows Excel 2013 and Excel for Mac 2011, but should apply to 2007+.

# Example

```VB.net
' Timezone: EST (UTC-5:00), DST: True (+1:00) -> UTC-4:00
Dim LocalDate As Date
Dim UtcDate As Date
Dim Iso As String

LocalDate = DateValue("Jan. 2, 2003") + TimeValue("4:05:06 PM")
UTCDate = UtcConverter.ConvertToUtc(LocalDate)

Debug.Print VBA.Format$("yyyy-mm-ddTHH:mm:ss.000T", UtcDate)
' -> "2003-01-02T20:05:06.000Z"

Iso = UtcConverter.ConvertToIso(LocalDate)
Debug.Print Iso
' -> "2003-01-02T20:05:06.000Z"

LocalDate = UtcConverter.ParseUtc(UtcDate)
LocalDate = UtcConverter.ParseIso(Iso)

Debug.Print VBA.Format$("m/d/yyyy h:mm:ss AM/PM")
' -> "1/2/2003 4:05:06 PM"
```
