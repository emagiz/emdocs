---
id: edit-job-manager
title: Edit Job Manager
sidebar_label: Job manager
---

The JobRepository provides CRUD operations on the meta-data, and the JobExplorer provides read-only operations on the meta-data. However, those operations are most useful when used together to perform common monitoring tasks such as stopping, restarting, or summarizing a Job, as is commonly done by batch operators.

---
id: edit-job-manager
title: Edit Job Manager
sidebar_label: Job Explorer
---

The most basic need before any advanced features is the ability to query the repository for existing executions. This functionality is provided by the JobExplorer interface. JobExplorer is a read-only version of the JobRepository, and like the JobRepository, it can be easily configured.

