## Version 4.0.0 ##

Release Date : 2021-04-08

### Known Issues

If you're using the docker images, then you may encounter issues with the zulu based images that look like this: 
```
GenericConnectorServer Receiver.run
SEVERE: Unexpected IOException: java.net.SocketTimeoutException: Accept timed out
GenericConnectorServer Receiver.run
SEVERE: stopping server
```
We haven't been able to reproduce the issue consistently, our suggestion is that you switch to a different image in order to use remote JMX via JMXMP


### Key Highlights

- This Interlok version has been compiled for Java 11.
- The deprecated ProduceDestination & ConsumeDestination components have been removed and entirely replaced with simplified configuration elements.
- The Nashorn script engine is deprecated and you will recieve warnings if the EmbeddedScriptingService language is set to 'nashorn'.
- Lots of deprecated things have been removed; please execute --configtest (or use the parent gradle) with an existing 3.12 instance to see what might have been removed
- To mitigate against XXE, XML Services now use a restricted instance if you leave it null, which means the default underlying document factory will disable things like doctype and entity handling. This change will not break config directly, but it will break currently-working functionality if you are relying on those featured being defaulted on in some DocumentBuilderFactory implementations.
- interlok-xinclude has been marked as deprecated and due to be removed in Interlok 5.0.0; One of the reasons for this, is the way the Interlok UI handles relative paths; it is not always compatible with the Interlok xincludes pre-processors.    
- Several optional components have been removed, either because there is an improved replacement or they are not compatible with Java 11 as they are too old, or they are unloved components:
  - interlok-swiftmq
  - interlok-socket
  - interlok-variodoc
  - interlok-kubernetes-metrics
  - interlok-kubernetes-prometheus
  - interlok-profiler-prometheus
  - interlok-as2
  - interlok-ironmq
  - interlok-oftp
  - interlok-reliable-messaging
  - interlok-salesforce
  - interlok-sonicmf
  - interlok-shell
  - interlok-vcs-command-line
  - interlok-container
  - interlok-actional-interceptor
  - interlok-actional-stabiliser
  - interlok-vcs-subversion

### Bugs

- 'INTERLOK-2577' - Interlok-webservice-cxf does not work with Java 9 +
- 'INTERLOK-3572' - NPE - DefinedJmsProducer
- 'INTERLOK-3595' - BAPI Producer does not work inside a RFC Servicelist
- 'INTERLOK-3702' - interlok retry-via-jetty setting reporting-endpoint does not work
- 'INTERLOK-3712' - UI Service Tester - unable to edit 'Test Adapter Type' in ui as Helpers is required field (but empty)
- 'INTERLOK-3714' - Cassandra - The connection is never started/initialised and does not support shared connection.
- 'INTERLOK-3716' - Artemis management component package name is wrong
- 'INTERLOK-3719' - move-file-service 'Move Directory must not be null' yet it's an advanced field with a default.
- 'INTERLOK-3724' - Prometheus Profiler Metrics Only Returns One Workflow
- 'INTERLOK-3732' - interlok-profiler-prometheus pom desc is missing
- 'INTERLOK-3735' - Rest metrics - NPE
- 'INTERLOK-3737' - Interlok Mail - Producer log the password used in the smtp url
- 'INTERLOK-3738' - Proagrica-NIC: MessageRouter IndexOutOfBoundsException when a route is "complete"
- 'INTERLOK-3743' - SwiftMQ - Archive & Remove
- 'INTERLOK-3748' - FileParameter no longer supports the same behaviour as "destination".
- 'INTERLOK-3752' - JClouds Blobstore - Exception when running ListBlobs with prefix using aws-s3 provider
- 'INTERLOK-3766' - Ui Config - fixed broken documentation links on the settings editor

### Improvements

- 'INTERLOK-3573' - XML Services should be using a restricted document factory by default
- 'INTERLOK-3578' - Azure Datalake create directory hierarchy when uploading
- 'INTERLOK-3589' - UI Component Search Indexer - ensure indexer works with the v4 javadocs
- 'INTERLOK-3594' - Failover - update language used in project (master/slave to primary/secondary)
- 'INTERLOK-3709' - Remove variodoc from the Interlok 4 release process
- 'INTERLOK-3728' - xincludes - mark interlok-xincludes as deprecated (for removal in 5.0)
- 'INTERLOK-3730' - UI Dashboard - remove the adapter's load config button
- 'INTERLOK-3739' - Proagrica-NIC : Support selection of topics vs queues
- 'INTERLOK-3744' - Update documentation for prometheus / profiler
- 'INTERLOK-2529' - Build all components using Java 11
- 'INTERLOK-3272' - Jenkins jobs for V4.
- 'INTERLOK-3596' - docker snapshot images should be baselined on java 11
- 'INTERLOK-3597' - Merge develop-java11 into develop and change all the Jenkins jobs
- 'INTERLOK-3601' - Test interlok-activemq features using Java 11
- 'INTERLOK-3602' - Test interlok-amqp features using Java 11
- 'INTERLOK-3603' - Test interlok-artemis features using Java 11
- 'INTERLOK-3604' - Test interlok-apache-http features using Java 11
- 'INTERLOK-3605' - Test interlok-aws-kinesis features using Java 11
- 'INTERLOK-3606' - Test interlok-aws-kms features using Java 11
- 'INTERLOK-3607' - Test interlok-aws-s3 features using Java 11
- 'INTERLOK-3608' - Test interlok-aws-sns features using Java 11
- 'INTERLOK-3609' - Test interlok-aws-sqs features using Java 11
- 'INTERLOK-3610' - Test interlok-azure-cosmosdb features using Java 11
- 'INTERLOK-3611' - Test interlok-azure-mail features using Java 11
- 'INTERLOK-3612' - Test interlok-azure-onedrive features using Java 11
- 'INTERLOK-3613' - Test interlok-ehcache features using Java 11
- 'INTERLOK-3614' - Test interlok-apache-geode features using Java 11
- 'INTERLOK-3615' - Test interlok-jsr107-cache features using Java 11
- 'INTERLOK-3616' - Test interlok-azure-datalake features using Java 11
- 'INTERLOK-3618' - Create interlok-jslt sub-module of interlok-json
- 'INTERLOK-3619' - Test interlok-elastic-common/interlok-elastic-rest features using Java 11
- 'INTERLOK-3620' - Test interlok-cassandra features using Java 11
- 'INTERLOK-3621' - Test interlok-cluster-manager features using Java 11
- 'INTERLOK-3622' - Test interlok-csv features using Java 11
- 'INTERLOK-3623' - Test interlok-csv-json features using Java 11
- 'INTERLOK-3624' - Test interlok-filesystem features using Java 11
- 'INTERLOK-3625' - Test interlok-gcloud-pubsub features using Java 11
- 'INTERLOK-3626' - Test interlok-excel features using Java 11
- 'INTERLOK-3627' - Test interlok-exec features using Java 11
- 'INTERLOK-3628' - Test interlok-expressions features using Java 11
- 'INTERLOK-3629' - Test interlok-flatfile features using Java 11
- 'INTERLOK-3630' - Test interlok-hpcc features using Java 11
- 'INTERLOK-3631' - Test interlok-flyway features using Java 11
- 'INTERLOK-3632' - Test interlok-jmx-activemq features using Java 11
- 'INTERLOK-3633' - Test interlok-jmx-amqp features using Java 11
- 'INTERLOK-3634' - Test interlok-jmx-jms-stubs features using Java 11
- 'INTERLOK-3635' - Test interlok-jmx-solace features using Java 11
- 'INTERLOK-3636' - Test interlok-jmx-rabbitmq features using Java 11
- 'INTERLOK-3637' - Test interlok-jclouds-blobstore features using Java 11
- 'INTERLOK-3638' - Test interlok-jclouds-aws-sts features using Java 11
- 'INTERLOK-3639' - Test interlok-json features using Java 11
- 'INTERLOK-3640' - Test interlok-json-streaming features using Java 11
- 'INTERLOK-3641' - Test interlok-json-web-token features using Java 11
- 'INTERLOK-3642' - Test interlok-jq features using Java 11
- 'INTERLOK-3643' - Test interlok-kie features using Java 11
- 'INTERLOK-3644' - Test interlok-kafka features using Java 11
- 'INTERLOK-3645' - Test interlok-jruby features using Java 11
- 'INTERLOK-3646' - Test interlok-mongodb features using Java 11
- 'INTERLOK-3647' - Test interlok-mqtt features using Java 11
- 'INTERLOK-3648' - Test interlok-kubernetes-prometheus features using Java 11
- 'INTERLOK-3649' - Test interlok-kubernetes-metrics features using Java 11
- 'INTERLOK-3650' - Test interlok-mail features using Java 11
- 'INTERLOK-3651' - Test interlok-nats features using Java 11
- 'INTERLOK-3652' - Test interlok-oauth-azure features using Java 11
- 'INTERLOK-3653' - Test interlok-oauth-generic features using Java 11
- 'INTERLOK-3654' - Test interlok-oauth-gcloud features using Java 11
- 'INTERLOK-3655' - Test interlok-oauth-salesforce features using Java 11
- 'INTERLOK-3656' - Test interlok-pgp features using Java 11
- 'INTERLOK-3657' - Test interlok-pdf features using Java 11
- 'INTERLOK-3658' - Test interlok-okhttp features using Java 11
- 'INTERLOK-3659' - Test interlok-socket features using Java 11
- 'INTERLOK-3660' - Test interlok-webservice-cxf features using Java 11
- 'INTERLOK-3661' - Test interlok-vcs-git features using Java 11
- 'INTERLOK-3662' - Test interlok-vertx features using Java 11
- 'INTERLOK-3663' - Test interlok-sshtunnel features using Java 11
- 'INTERLOK-3664' - Test interlok-stax features using Java 11
- 'INTERLOK-3665' - Test interlok-swift features using Java 11
- 'INTERLOK-3666' - Test interlok-varsub features using Java 11
- 'INTERLOK-3667' - Test interlok-xinclude features using Java 11
- 'INTERLOK-3668' - Test interlok-rest-cluster features using Java 11
- 'INTERLOK-3669' - Test interlok-rest-health-check features using Java 11
- 'INTERLOK-3670' - Test interlok-rest-prometheus features using Java 11
- 'INTERLOK-3671' - Test interlok-service-tester (inc. submodules gradle, json, wiremock & xml) features using Java 11
- 'INTERLOK-3672' - Test interlok-monitor-agent / interlok-profiler features using Java 11
- 'INTERLOK-3673' - Test interlok-profiler-prometheus features using Java 11
- 'INTERLOK-3674' - Test interlok/proagrica-nic features using Java 11
- 'INTERLOK-3675' - Test interlok-core (boot, common, logging etc) features using Java 11
- 'INTERLOK-3676' - Test adaptris-saxon-extensions features using Java 11
- 'INTERLOK-3678' - Test interlok-edi-legacy features using Java 11
- 'INTERLOK-3679' - Test interlok-edi-stream features using Java 11
- 'INTERLOK-3680' - Test interlok-failover features using Java 11
- 'INTERLOK-3681' - Test interlok-jmx-sonicmq features using Java 11
- 'INTERLOK-3682' - Test interlok-jms-sonicmq features using Java 11
- 'INTERLOK-3683' - Test interlok-jms-oracleaq features using Java 11
- 'INTERLOK-3684' - Test interlok-licensing (inc. demo and stub submodules) features using Java 11
- 'INTERLOK-3685' - Test interlok-msmq-javonet features using Java 11
- 'INTERLOK-3686' - Test interlok-new-relic features using Java 11
- 'INTERLOK-3687' - Test interlok-sap features using Java 11
- 'INTERLOK-3688' - Test interlok-vcs-subversion features using Java 11
- 'INTERLOK-3689' - Test interlok-webspheremq features using Java 11
- 'INTERLOK-3690' - Test interlok-triggered features using Java 11
- 'INTERLOK-3691' - Test interlok-solace features using Java 11
- 'INTERLOK-3692' - Test interlok-tibco features using Java 11
- 'INTERLOK-3693' - Test interlok-swiftmq features using Java 11
- 'INTERLOK-3694' - Test interlok-variodoc features using Java 11
- 'INTERLOK-3695' - Test interlok-xml-security features using Java 11
- 'INTERLOK-3696' - Test interlok-xa-activemq features using Java 11
- 'INTERLOK-3697' - Test interlok-xa-atomikos features using Java 11
- 'INTERLOK-3698' - Test interlok-xa-jms features using Java 11
- 'INTERLOK-3699' - Test interlok-xa-solace features using Java 11
- 'INTERLOK-3700' - Test interlok-xa-tibco features using Java 11
- 'INTERLOK-3701' - Test interlok-xa-wmq features using Java 11
- 'INTERLOK-3703' - Test interlok-jolokia features using Java 11
- 'INTERLOK-2331' - MS Graph - What can we do with the mail component?
- 'INTERLOK-2750' - com.sun.tools.doclets.Taglet missing in Java 11
- 'INTERLOK-2903' - Add Automatic-Module-Name to all manifest files.
- 'INTERLOK-2913' - UI Version Upgrade - Bump spring from 4.3.22.RELEASE to the latest 5.1
- 'INTERLOK-2963' - UI - Upgrade Derby DB to 10.15.2.0
- 'INTERLOK-3268' - Web UI - gradle
- 'INTERLOK-3270' - JMX -> Jolokia
- 'INTERLOK-3271' - Opinionated x-include style config
- 'INTERLOK-3273' - Switch all projects to build with Java 11
- 'INTERLOK-3275' - Move from bitbucket to gitlab.agb
- 'INTERLOK-3296' - interlok-stubs should be its own top level project
- 'INTERLOK-3327' - Interlok workflow API
- 'INTERLOK-3363' - Migrate SAP build from ant to gradle
- 'INTERLOK-3439' - JDK 11 : Nashorn deprecated, has gone away in JDK 15
- 'INTERLOK-3457' - JSLT - JSON Query and Transformation Language
- 'INTERLOK-3509' - Support JSON_LINES as output method for completeness
- 'INTERLOK-3516' - Investigate open-telemetry
- 'INTERLOK-3535' - UI Service Tester - Wiremock testcase doesn't work when using port property.
- 'INTERLOK-3536' - UI Service Tester - Look to expose embedded-jmx-test-client features
- 'INTERLOK-3548' - Standardise on the "short name" in terms of convention
- 'INTERLOK-3551' - New PW: alternative required
- 'INTERLOK-3552' - Upgrade interlok-xa from mockito:1.10.19 to mockito-core:3
- 'INTERLOK-3556' - UI Version Upgrade - Update gridtsack to a later version
- 'INTERLOK-3558' - Remove/Exclude Optional Components that are deprecated (and marked 'be removed interlok 4.0')
- 'INTERLOK-3559' - Remove items marked with @ConfigDeprecated(version="4")
- 'INTERLOK-3560' - Create a Jolokia management component that will eventually replace the JMXMP connector
- 'INTERLOK-3563' - JavaFx Installer - Switch to the Java11 version of the installer and make sure it still works
- 'INTERLOK-3564' - Installer changes update (no-installanywhere)
- 'INTERLOK-3566' - Remove the deprecated produce-destination / consume-destination
- 'INTERLOK-3567' - Replace the object metadata features of JmsReplyToDestination
- 'INTERLOK-3571' - interlok-workflow-rest-services should become a multi-module
- 'INTERLOK-3574' - Prometheus JVM Metrics
- 'INTERLOK-3575' - Promethes Metrics Structure
- 'INTERLOK-3576' - UI - embedded javadocs tooltips not working in v4
- 'INTERLOK-3582' - UI - Upgrade jetty to 9.4.36.v20210114, flyway to 7.7.0, mockito to 3.7.7 and spotbug to 4.2.0
- 'INTERLOK-3585' - Deprecate the interlok-vcs-subversion project
- 'INTERLOK-3587' - Prometheus Profiler Metrics Storage
- 'INTERLOK-3590' - UI - Support the new PW password encoding in the config page
- 'INTERLOK-3591' - Interlok XA - Bump ibm mq to 9.1.5.0 to fix vulnerability
- 'INTERLOK-3600' - Java 11 - Test behaviour of Interlok components using Java 11
- 'INTERLOK-3704' - UI - Dependency vulnerabilities in shiro, httpclient and guava
- 'INTERLOK-3707' - UI - create missing optional component icons
- 'INTERLOK-3708' - Rename interlok-fx-installer to interlok-installer
- 'INTERLOK-3715' - UI - Disable the Profiler Monitor page as we are not going to maintain it anymore.
- 'INTERLOK-3717' - Bump interlok-templates-tester to Java 11
- 'INTERLOK-3718' - Interlok-Profiler-Prometheus should be removed?
- 'INTERLOK-3723' - interlok-monitor-agent: JmxEventPropagator update whats debug vs trace
- 'INTERLOK-3725' - Prometheus JVM Metrics "Incomplete"
- 'INTERLOK-3727' - UI - Bump flyway-core to 7.5.4, commons-net to 3.8.0, snakeyaml to 1.28, swagger-v3 to 2.1.7, spring to 5.3.4 and mockito to 3.8.0
- 'INTERLOK-3734' - Nashorn - Add a doc page to explain about Nashorn being deprecated and how to use GraalJS
- 'INTERLOK-3740' - JCraft - JSCH update
- 'INTERLOK-3742' - Profiling Memory Issues
- 'INTERLOK-3745' - Interlok Templates - Check all the templates and fix them if they use deprecated components.
- 'INTERLOK-3753' - UI Salesforce - Fix UI salesforce producer template to not use destination
- 'INTERLOK-3765' - Installer - Add a new column in the list display if a component is licensed
- 'INTERLOK-3755' - Change the download page process to use zip/tar files.
- 'INTERLOK-3760' - Update  xml-security project, change the iaik dependencies to be optional
- 'INTERLOK-3759' - Update saxon-extensions project, so the groupId is 'com.proagrica'
