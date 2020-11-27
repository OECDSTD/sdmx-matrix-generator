It's about time I add a release notes document.
# 27/11/2020
## New
- Add MAXTEXTATTRIBUTELENGTH DSD annotation
- Make Constraint IDs editable. When prefilling show them on Dataflow worksheet
- Add named ranges to make it easier for programs that wrap the application
- Add UNIT_MEASURE_CONCEPTS Dataflow annotation
- Add DSD annotations

## Fixed
- Dimension with role D(Frequency) is skipped when generating attachment relationship for time-series attribute #68
- Prefill from Rest API goes in error with Excel language settings "German"
- Locale language setting in Excel different from English #53
- Prefill function errors when regional settings include separators that are incompatible with adding hyperlinks
- Prefilling Annotations errors because it assumes several properties are mandatory. They're not in SDMX
