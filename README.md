# Using MARC prediction patterns

MARC provides a powerful, but almost indecipherable language for documenting 
the publication schedule of serial publications. These patterns can be used
to great effect in ILS/LMSs to generate records for expected serial issues.

## About this document

I wrote most of the current patterns over the summer of 2016 for use in 
[Alma](http://www.exlibrisgroup.com/products/alma-library-services-platform/). 
Some of the patterns may be less than ideal because they were created while 
I was learning how prediction patterns worked or because they were written 
around bugs in Alma that may have been fixed since that summer or are not present
in other systems that support prediction patterns. All the examples
below were functional, despite any flaws, and used at the
[Wartburg College library](http://www.wartburg.edu/library).

The initial draft of this document was written as a cheat sheet and reference for 
myself. Since then, I've shared it on the Alma mailing list and it has been incorporated
in official Alma [documentation materials](https://knowledge.exlibrisgroup.com/Alma/Training/Extended_Training/Presentations_and_Documents_-_Serials).
Because librarians using other library software may be able to make use of the
prediction patterns or may be willing to contribute to this document by adding
their own examples or correcting errors, I've made the current version available
on [GitHub](https://github.com/wtee/Using-MARC-prediction-patterns).

## Introduction to MARC prediction patterns

Prediction patterns are used in mark fields 853-855.

The official documentation for prediction patterns can be found here: 
[http://loc.gov/marc/holdings/hd853855.html](http://loc.gov/marc/holdings/hd853855.html).
If you want to really understand MARC prediction patterns, you'll need to refer to the official 
documentation.

### A brief overview of commonly-used subfields

`$$a` volume (top level enumeration)
`$$b` number/issue (secondary enumeration)
`$$u` issues per year
`$$v` numbering pattern (repeating or continuous)
`$$w` periodicity (monthly, weekly, etc.)
`$$x` when new volume starts
`$$y` regularity pattern

## Examples

### Bimonthly

Bimonthly, 6 issues per volume, combines every two months starting with Jan/Feb, 
new volume in January (hack of monthly ($$w m rather than $$w b) to get joint months)
`$$a v. $$b no. $$u 6 $$v r $$i (year) $$j (month) $$w m $$x 01 $$y cm01/02,03/04,05/06,07/08,09/10,11/12 $$8 1`
Bimonthly, 6 issues per volume, non-combined months, new volume in September
`$$a v. $$b no. $$u 6 $$v r $$i (year) $$j (month) $$w b $$8 1 $$x 09`
Bimonthly, 6 issues per year, combines every two months, new volume in January
`$$a v. $$b no. $$u 6 $$v r $$i (year) $$j (month) $$w b $$8 1`
Bimonthly, 6 issues per year, combines every two months, new volume in September
`$$a v. $$b no. $$u 6 $$v r $$i (year) $$j (month) $$w b $$8 1 $$x 09`

### Biweekly

Biweekly, 26 issues per volume, month and day used in chronology, new volume in January
`$$a v. $$b no. $$u 26 $$v r $$i (year) $$j (month) $$k (day) $$w e $$8 1 $$x 01`
Biweekly, continuous enumeration
`$$a Issue $$v c $$i (year) $$j (month) $$k (day) $$w e $$8 1`
Biweekly, 2 volumes per year, 13 issues per volume, new volumes in January and July
`$$a v. $$b no. $$u 13 $$v r $$i (year) $$j (month) $$k (day) $$w e $$8 1 $$x 01,07`

### Monthly

Monthly, 12 issues per volume, new volume in January
`$$a v. $$b no. $$u 12 $$v r $$i (year) $$j (month) $$w m $$8 1 $$x 01`
Monthly, 12 issues per volume, new volume in August
`$$a v. $$b no. $$u 12 $$v r $$i (year) $$j (month) $$w m $$8 1 $$x 08`
Monthly, 6 issues per volume, new volume in January and in July (2 volumes per year)
`$$a v. $$b no. $$u 6 $$v r $$i (year) $$j (month) $$w m $$x 01,07 $$8 1`
Monthly, 11 issues per volume, new volume in November, combined Dec/Jan issue
`$$a v. $$b no. $$u 11 $$v r $$i (year) $$j (month) $$w m $$x 11 $$y cm12/01 $$8 1`
Monthly, 11 issues per volume, new volume in January, combined Jan/Feb issue
`$$a v. $$b no. $$u 11 $$v r $$i (year) $$j (month) $$w m $$x 01 $$y cm01/02 $$8 1`
Monthly, 11 issues per volume, combines Jun/Jul, new volume in August
`$$a v. $$b no. $$u 11 $$v r $$i (year) $$j (month) $$w m $$x 08 $$y cm06/07 $$8 1`
Monthly, 11 issues per volume, combines Jun/Jul, new volume in January
`$$a v. $$b no. $$u 11 $$v r $$i (year) $$j (month) $$w m $$y cm06/07 $$8 1 $$x 01`
Monthly, 10 issues per volume, combined Jan/Feb and Jul/Aug issues, new volume in January
`$$a v. $$b no. $$u 10 $$v r $$i (year) $$j (month) $$w m $$y cm01/02,07/08 $$x 01 $$8 1`
Monthly, 10 issues per volume, omits July, August, new volume in September
`$$a v. $$b no. $$u 10 $$v r $$i (year) $$j (month) $$w m $$x 09 $$y om07,08 $$8 1`
Monthly, 10 issues per volume, combines Jan/Feb and Jul/Aug, new volume in January
`$$a v. $$b no. $$u 10 $$v r $$i (year) $$j (month) $$w m $$x 01 $$y cm01/02,07/08 $$8 1`
Monthly, 9 issues per year, combines May/Jun, Jul/Aug, Nov/Dec, new volume in September
`$$a v. $$b no. $$u 9 $$v r $$i (year) $$j (month) $$w m $$y  cm05/06,07/08,11/12 $$8 1 $$x 09`
Monthly, 5 issues per volume, 2 volumes per year, combined Jan/Feb and July/Aug issues, 
new volumes in January and August (2 volumes per year)
`$$a v. $$b no. $$u 10 $$v r $$i (year) $$j (month) $$w m $$8 1 $$y cm01/02,06/07 $$x 01,08`
Monthly, 9 issues per volume, omits July, combined May/Jun, Nov/Dec, new volume in January
`$$a v. $$b no. $$u 9 $$v r $$i (year) $$j (month) $$w m $$y om07 $$y cm05/06,11/12 $$x 01 $$8 1`
Monthy, 9 issues per volume, omits July, August, combines May/Jun, new volume in September
`$$a v. $$b no. $$u 9 $$v r $$i (year) $$j (month) $$w m $$y cm05/06 $$y om07,08 $$8 1 $$x 09`

### Quarterly

Quarterly, 4 issues per volume, season name used in chronology, new volume in Spring
`$$a v. $$b no. $$u 4 $$v r $$i (year) $$j (season) $$w q $$8 1 $$x 21`
Quarterly, 4 issues per volume, season name used in chronology, new volume in Winter
`$$a v. $$b no. $$u 4 $$v r $$i (year) $$j (season) $$w q $$8 1 $$x 24`
Quarterly, 4 issues per volume, months used in chronology, new volume in October
`$$a v. $$b no. $$u 4 $$v r $$i (year) $$j (month) $$w q $$8 1 $$x 10`
Quarterly, 4 issues per volume, months used in chronology, new volume in October, 
published Jan/Mar/Jun/Oct (This is actually a hack of a monthly pattern ($$w m instead of $$w q) 
because the quarterly pattern wouldn’t play nice with this unusual publication schedule)
`$$a v. $$b no. $$u 4 $$v r $$i (year) $$j (month) $$w m $$8 1 $$y om02,04,05,07,08,09,11,12 $$x 10`
Quarterly, 4 issues per year, seasons used in chronology, single continuous enumeration
`$$a no. $$u 4 $$v c $$i (year) $$j (season) $$w q $$8 1`
Quarterly, 4 issues per year, months used in chronology, new volume in December
`$$a v. $$b no. $$u 4 $$v r $$i (year) $$j (month) $$w q $$8 1 $$x 12`

### Triannual

Triannual, 3 issues per year, seasons used in chronology, new volume in Spring
`$$a v. $$b no. $$u 3 $$v r $$i (year) $$j (season) $$w t $$y ps21,22,23 $$8 1 $$x 21`
Triannual, 3 issues per year, seasons used in chronology, new volume in Autumn 
(hack of quarterly pattern because predictions weren’t working for some reason)
`$$a v. $$b no. $$u 3 $$v r $$i (year) $$j (season) $$w q $$y os21 $$8 1 $$x 23`
Triannual, 3 issues per year, seasons used in chronology, new volume in Spring 
(hack of quarterly pattern because predictions weren’t working for some reason)
`$$a v. $$b no. $$u 3 $$v r $$i (year) $$j (season) $$w q $$y os23 $$8 1 $$x 21`

### Weekly

Weekly, 52 issues per year, no volume, issue numbering restarts in January
`$$b no. $$u 52 $$v r $$i (year) $$j (month) $$k (day) $$w w $$x 01 $$8 1`
Weekly, 52 issues per volume, new volume in January
`$$a v. $$b no. $$u 52 $$v r $$i (year) $$j (month) $$k (day) $$w w $$8 1 $$x 01`
