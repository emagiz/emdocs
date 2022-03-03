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

# Cloud security

In the last microlearning, we focused on runtime security. In this microlearning, the focus will be on various aspects of cloud security when running your solution in the eMagiz cloud. We will focus on high-level security measurements within the cloud. We will look at the cloud setup, cloud location, cloud slot, cloud template, and the carwash in the cloud.

Should you have any questions, please contact academy@emagiz.com.

- Last update: August 3th, 2021
- Required reading time: 6 minutes

## 1. Prerequisites
- Intermediate knowledge of the eMagiz platform

## 2. Key concepts
This microlearning centers on cloud security.

With cloud security, we mean: The measures that are taken within the context of the eMagiz cloud to secure the eMagiz cloud properly for our customers

- The key aspects are:
    - Running in the cloud works for both single as well as double lane setups
    - The cloud template governs how the various components are deployed within the cloud
    - The carwash enables additional security measures

##### Theory
  
## 3. Cloud security

In the last microlearning, we focused on runtime security. In this microlearning, the focus will be on various aspects of cloud security when running your solution in the eMagiz cloud. We will focus on high-level security measurements within the cloud. We will look at the cloud setup, cloud location, cloud slot, cloud template, and the carwash in the cloud.

- The key aspects are:
    - Running in the cloud works for both single as well as double lane setups
    - The cloud template governs how the various components are deployed within the cloud
    - The carwash enables additional security measures

### 3.1 Cloud setup

In the picture shown below, you see a standard double-lane setup of an eMagiz instance within the eMagiz Cloud. A single-lane setup looks similar but only consists of one core machine.
This gives a good insight into how messages are flowing through the cloud, which measures are taken for monitoring and auto-healing, and where data is temporarily stored 'in transit'. 

<p align="center"><img src="../../img/microlearning/intermediate-portal-security-cloud-security--cloud-setup-emagiz.png"></p>

We would like to use this picture to explain certain components within the cloud from a security perspective. We will start at the outside and work our way inwards.

### 3.2 Cloud location

Within the AWS cloud, there are several regions where your cloud setup can be running. Examples of these regions are us-east-1, af-south-1, ap-northeast-1, eu-central-1.

As you can see in the picture eMagiz cloud slots are running within the eu-central-1 region. This region is located in Frankfurt and falls therefore under European data and security laws such as the GDPR.

### 3.3 Cloud slot (VPC)

Within this region, a unique cloud slot per customer is assigned. In the picture, this is represented as a Virtual Private Cloud (VPC). Setting up a VPC provides a logically isolated section of the AWS Cloud where AWS resources can be launched in a virtual network defined. There is complete control over the virtual networking environment, including a selection of the IP address range, creation of subnets, and configuration of route tables and network gateways.

Incoming data from the internet passes through a load balancer to route data randomly to one of the core machines containing the runtimes holding the process flows. The setup of a VPC is governed by what is called a Cloud Template.

### 3.4 Cloud template
 
This Cloud Template, designed by eMagiz defines the setup of the cloud instance. The following parts of the cloud setup are configured here:

- Java version
- OS version (Linux)
- Runtime version
- Auto healing
- Monitoring
- Notification options

Staying on the latest cloud template version guards yourself against vulnerabilities in older versions of Java and OS for example. In addition, it gives the user more options for monitoring the health of the cloud environment reducing the risk of a loss of availability of data (promptly) without compromising the integrity of the data.

As one can imagine anyone with access to the machines where runtimes are running on can compromise the availability, integrity, and confidentiality of data. eMagiz offers two locations where eMagiz runtimes can be installed. Per location, specific security measures are discussed that should be taken to ensure the availability, integrity, and confidentiality of the data. More information on cloud templates can be found [here](novice-emagiz-cloud-management-cloud-templates-explained.md)

### 3.5 Carwash

All data that is exchanged between an external system and a cloud instance goes through the carwash that protects all client instances from harm and routes data to the correct client instance.

In terms of security this means the following benefits from being behind the carwash:

- The connection is HTTPS instead of HTTP via the emagiz.com certificate
- Your VMs are protected because the carwash only allows relevant traffic to get through
- It gives you the ability to submit a certificate request via the Support portal to ensure two-way SSL (both server as well as client certificate validation).

##### Practice

## 4. Assignment

Verify if your project adheres to the security rules specified above.

## 5. Key takeaways

- The key aspects are:
    - Running in the cloud works for both single as well as double lane setups
    - The cloud template governs how the various components are deployed within the cloud
    - The carwash enables additional security measures

##### Solution

## 6. Suggested Additional Readings

If you are interested in this topic and want more information please check out the [Security Guide](../fundamental/fundamental-emagiz-security-guide.md)

## 7. Silent demonstration video

As this is a more theoretical microlearning we have no video for this

</div>
</main>
</div>
</div>