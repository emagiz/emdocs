---
id: job
title: Job
sidebar_label: Job
---

Each <i>Job</i> may be associated with multiple JobInstances, each of which is defined uniquely by its particular <code>JobParameters</code> that are used to start a batch job.

Each run of a <code>JobInstance</code> is referred to as a <code>JobExecution</code>. Each JobExecution typically tracks what happened during a run, such as current and exit statuses, start and end times, etc.

A Job is executed by a <code>JobLauncher</code>, and metadata about configured and executed jobs is stored in a <code>JobRepository</code>.


Use steps to configure the content of the job. The order of the other steps does not matter, but the first step listed is always the first step executed by the Job. Make sure that all other steps are 'reachable' by calling them using the next property in another step.

