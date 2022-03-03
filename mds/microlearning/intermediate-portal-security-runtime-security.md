<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/intermediate-portal-security-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# Runtime security

A key part of the eMagiz architecture is the runtime. The runtime holds all flows related to a particular process or system. Without runtimes to run your flows on there would be no processing of data. In this microlearning, we will zoom in on the runtime level to discern how the security is governed. While doing this we will make a distinction between on-premise and cloud deployments.

Should you have any questions, please contact academy@emagiz.com.

- Last update: August 3th, 2021
- Required reading time: 6 minutes

## 1. Prerequisites
- Intermediate knowledge of the eMagiz platform

## 2. Key concepts
This microlearning centers on runtime security.

With runtime security, we mean: The measures that are taken to secure the information and related data on runtime level

- The key aspects are:
    - The security measures differ when comparing an on-premise deployment with a cloud deployment
    - Having appropriate rights is key
    - When running on-premise the security becomes a joint-effort
    - Normal users cannot access the install base in the eMagiz Cloud but execute actions on the eMagiz Cloud via the portal

##### Theory
  
## 3. Runtime security

A key part of the eMagiz architecture is the runtime. The runtime holds all flows related to a particular process or system. Without runtimes to run your flows on there would be no processing of data. In this microlearning, we will zoom in on the runtime level to discern how the security is governed. While doing this we will make a distinction between on-premise and cloud deployments.

- The key aspects are:
    - The security measures differ when comparing an on-premise deployment with a cloud deployment
    - Having appropriate rights is key
    - When running on-premise the security becomes a joint-effort
    - Normal users cannot access the install base in the eMagiz Cloud but execute actions on the eMagiz Cloud via the portal

As one can imagine anyone with access to the machines where runtimes are running on can compromise the availability, integrity, and confidentiality of data. eMagiz offers two locations where eMagiz runtimes can be installed. Per location, specific security measures are discussed that should be taken to ensure the availability, integrity, and confidentiality of the data.

### 3.1 On-premise

On-premise means that the runtimes are running on a machine outside the direct control of eMagiz. This means that the machine is running under the control of the customer that implements eMagiz within their IT landscape.

Because the machine is outside the direct scope of control of eMagiz it becomes a joint effort between eMagiz and you as a customer to make sure that not everyone can access this machine. This becomes even more important when working with file-based actions as part of your integration. 
Advice would be to govern this via an IDP (i.e. Azure AD) so you can set up roles that have access to the machine or parts of the machine (i.e. some files).


#### Rights for installing

To install a runtime on an on-premise you need sufficient rights to execute (batch) programs. This means that the user needs administrator rights on that specific machine to correctly install the runtime.

#### Rights for running

In Windows, a service account is needed to be able to run a Windows Service (in this case the runtime you have installed). This service account is different compared to the user that does the installing of the runtime.
There are two options on this level:
    
- Use the local system account. This account has sufficient rights to run the service and can therefore be used for everything. Less work to configure, more impact on the integrity of data when the account gets compromised.
- Use a specific service account per runtime. This way you limit the power of users to a specific runtime making you less vulnerable if this account gets compromised.

In Linux, the service will be running under the local system account as per default.

### 3.2 Cloud

In the eMagiz cloud, the access is restricted to those who have a legitimate reason to access it based on the SLA level agreements between customers and eMagiz. This means support engineers, consignment employees, and your bus owner have access to your specific cloud setup.
This access is per role furthermore limited. This means that consignment employees and bus owners can only see the logging of the runtimes on the machine and the ability to start/stop machines.

Support engineers can see more to analyze problems on a lower level.

All other users don't have access to the cloud setup as there is no need for access because they can perform the relevant actions on the cloud via the eMagiz portal. For more information on how please see [eMagiz Cloud Management](novice-emagiz-cloud-management-index.md).

#### Rights for installing

To install a runtime in the cloud you need sufficient rights within the Deploy phase of eMagiz.

#### Rights for running

The VPC in the cloud runs on a Linux environment. Therefore the same logic applies as specified above for Linux systems. In Linux, the service will be running under the local system account as per default.

##### Practice

## 4. Assignment

Verify if your project adheres to the security rules specified above.

## 5. Key takeaways

- The key aspects are:
    - The security measures differ when comparing an on-premise deployment with a cloud deployment
    - Having appropriate rights is key
    - When running on-premise the security becomes a joint-effort
    - Normal users cannot access the install base in the eMagiz Cloud but execute actions on the eMagiz Cloud via the portal

##### Solution

## 6. Suggested Additional Readings

If you are interested in this topic and want more information please check out the [Security Guide](../fundamental/fundamental-emagiz-security-guide.md)

## 7. Silent demonstration video

As this is a more theoretical microlearning we have no video for this

</div>
</main>
</div>
</div>