---
id: edit-simple-job-launcher
title: Edit Simple Job Launcher
sidebar_label: Simple job launcher
---

Simple implementation of the JobLauncher interface. 

A <code>JobLauncher</code> represents a simple interface for launching a <code>Job</code> with a given set of <code>JobParameters</code>

There is only one required dependency of this Launcher, a <code>JobRepository</code>. The <code>JobRepository</code> is used to obtain a valid <code>JobExecution</code>. The <code>Repository</code> must be used because the provided Job could be a restart of an existing <code>JobInstance</code>, and only the Repository can reliably recreate it.

