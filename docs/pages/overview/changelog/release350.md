## Version 3.5.0 ##

Release Date : 2016-11-18

### Key Highlights

- Generate Interlok Config from YAML
- UI Log Monitor improvements
- Settings Editor 'Change Type' improvements
- Workflow & Service Clustering now available (via Vert.X)
- Service-Testing Framework: to allow unit testing of config XML
- Aggregating FTP Consumer which supports single and multi file pickup
- Support for alternative password encryption methods

### Bugs

- `INTERLOK-243` - Enum config values don't work with user friendly display name
- `INTERLOK-771` - VSC-Git Jars Not Delivered as part of baseline deliverable
- `INTERLOK-1086` - UI Config - support TransactionManager for shared components
- `INTERLOK-1106` - Change the default URL for javadocs
- `INTERLOK-1188` - UI Doc - Link to ui user security doc page in the ui api doc page is broken
- `INTERLOK-1191` - Validation-api breaks Webservices and Restful components
- `INTERLOK-1193` - XSLT Broken: java.lang.NoClassDefFoundError: org/apache/commons/lang3/StringUtils
- `INTERLOK-1195` - When loading an existing XML config into the UI and trying to apply it there is no OK box on both Safari and Chrome
- `INTERLOK-1196` - When logging in there is a glass fish error reported on the UI
- `INTERLOK-1197` - ClassCastException when using 3.4.1 with profiler based failover
- `INTERLOK-1198` - UI - Logging not working on edge because the event origin is undefined
- `INTERLOK-1204` - ant test does not work with openjdk-8-102 (azul systems)
- `INTERLOK-1227` - removed dependency on jquery flot js files
- `INTERLOK-1248` - Typo in the add adpter button title

### Improvements

- `INTERLOK-739` - Use Vert X as a wrapper for adapter components
- `INTERLOK-912` - UI VCS - add SSH support for VCS Profiles
- `INTERLOK-1009` - Support alternative password encryption methods
- `INTERLOK-1133` - Sort out the browser tab title
- `INTERLOK-1138` - Add a MBean to FSConsumer to display "how many files there are to process"
- `INTERLOK-1143` - JMS Translators - producer should default to the same message implementation as the consumer
- `INTERLOK-1146` - Make logging monitor tabs re-orderable
- `INTERLOK-1147` - UI API - Extend the REST API to "test service-collection"
- `INTERLOK-1151` - Create an AggregatingFTPConsumer
- `INTERLOK-1156` - UI Config - improve the change-type dropdown selector
- `INTERLOK-1167` - UI Config - Improve the auto generated component names
- `INTERLOK-1169` - UI - improve the welcome splash modal so it always fits on a single screen
- `INTERLOK-1171` - UI Logging - impl a performance mode for the log monitor page
- `INTERLOK-1173` - UI Config - Generate Adapter Config from swagger.yaml
- `INTERLOK-1175` - UI - Build Framework for Auto Generation of alerts
- `INTERLOK-1176` - UI - Add tests for ConfigController and AlertServiceImpl
- `INTERLOK-1202` - UI Footer - Display UI vesion number in the page footer
- `INTERLOK-1203` - interlok-json - Add JsonPath SyntaxIdentifier to be used in SyntaxBranchingService
- `INTERLOK-1205` - Allow CloneMessageServiceList to override metadata
- `INTERLOK-1207` - Interlok Service Testing Framework
- `INTERLOK-1209` - AddTimestampMetadataService should have a "lastmsg" variable.
- `INTERLOK-1211` - Extend FormattedMetadataDestination for key=value
- `INTERLOK-1215` - Interlok Service Test Template
- `INTERLOK-1217` - Add support for SSH via proxies for vcs-git
- `INTERLOK-1218` - Interlok Service Test - WireMock Helper
- `INTERLOK-1247` - Update JSonPathSplitterTest to create useful example-xml
- `INTERLOK-1250` - Change FileDataInputParameter & FileDataOutputParameter to use MessageDrivenDestination



