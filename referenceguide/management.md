
Manages debug logging and the collection of monitoring metrics by components in the flow.
To enable message channel and message handler metrics, add this support object to the message flow. Be aware that keeping track of metrics can negatively impact the flow's performance.

<code>MessageSources</code> only maintain counts, <code>MessageChannels</code> and <code>MessageHandlers</code> maintain duration statistics in addition to counts. One way to make use of these counts and statistics is to add an <i>MBean export</i> support object to the message flow, exposing the metrics through JMX. By default, eMagiz containers will then periodically collect all these JMX metrics and use them to feed the monitoring graphs in the eMagiz web portal.

In addition to metrics, you can control debug logging in the main message flow. It has been found that in very high volume applications, even calls to <code>isDebugEnabled()</code> can be quite expensive with some logging subsystems. You can disable all such logging to avoid this overhead; exception logging (debug or otherwise) are not affected by this setting.


Default logging enabled
Set to <code>false</code> to disable all logging in the main message flow, regardless of the log system category settings. This can improve performance.

Set to <code>true</code> to enable debug logging (if also enabled by the logging subsystem).


Counts enabled patterns
A comma-delimited list of patterns for components for which counts should be enabled.

A leading <code>!</code> negates the pattern match, e.g. <code>!foo*</code> means don't enabled counts for components where the name matches the pattern <code>foo*</code>. For components with names that match multiple patterns, the first pattern (from left to right) wins. For example, <code>!foo*, foox</code> will match all beans that don’t start with <code>foo</code>, except <code>foox</code>.

Default is <code>*</code>.


Default counts enabled
Enable or disable count metrics for components not matching one of the patterns in <i>counts enabled patterns</i>.


Stats enabled patterns
A comma-delimited list of patterns for components for which statistical metrics should be enabled.

A leading <code>!</code> negates the pattern match, e.g. <code>!foo*</code> means don't enable metrics for components where the name matches the pattern <code>foo*</code>. For components with names that match multiple patterns, the first pattern (from left to right) wins. For example, <code>!foo*, foox</code> will match all beans that don’t start with <code>foo</code>, except <code>foox</code>.

Default is <code>*</code>.


Default stats enabled
Enable or disable statistical metrics for components not matching one of the patterns in <i>stats enabled patterns</i>.

