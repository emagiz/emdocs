---
id: job-launching-gateway
title: Job Launching Gateway
sidebar_label: Job launching gateway
---

This Outbound Gateway is used to launch batch Jobs. The payload of messages to be processed MUST be an instance of <code>JobLaunchRequest</code>.

Note that you can create a <code>JobLaunchRequest</code> using a standard transformer with a SPEL expression like the one below

<pre>
new org.springframework.batch.integration.launch.JobLaunchRequest(@'s1.msg1.onramp.support.job',  new org.springframework.batch.core.JobParametersBuilder().
addString('input.file', payload.absolutePath).toJobParameters())
</pre>

