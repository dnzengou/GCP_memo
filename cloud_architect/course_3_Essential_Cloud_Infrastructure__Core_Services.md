# Essential Cloud Infrastructure: Core Services


The goal of these courses is:

* to remember and understand the **different GCP services** and **features** and also
* to be able to apply your knowledge, 
* to analyze requirements,
* to evaluate different options, and 
* to create your own services.

This course builds on the [Essential Cloud Infrastructure: Foundation](./cloud_architect/course_2_Essential_Cloud_Infrastructure__Foundation.md) course and enhances your study of architecting with Compute Engine. In this course, we start by talking about Cloud IAM, and you will administer Identity and Access Management for resources. Next, we’ll cover the different data storage services in GCP, and you will implement some of those services. Then, we’ll go over resource management, where you will manage and examine billing of GCP resources. Lastly, we’ll talk about resource monitoring, and you will monitor GCP resources using Stackdriver services. 


> "We want to welcome you to Architecting with Compute Engine".

## Content

[course intro video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/6Zi73/course-introduction)


* [Cloud Identity and Access Management (Cloud IAM)](#cloud-identity-and-access-management-cloud-iam)
    * [Organizations](#organizations)
    * [Folders: sub-organizations](#folders-sub-organizations)
    * [Roles](#roles)
    * [Demo: Create a Custom role in GCP](#demo-create-a-custom-role-in-gcp)
    * [Members](#members)
    * [Service Accounts](#service-accounts)
    * [Scopes](#scopes)
    * [Cloud IAM best practices](#cloud-iam-best-practices)
    * [Cloud IAP](#cloud-iap)
    * [Lab Intro: Cloud IAM](#lab-intro-cloud-iam)
* [Data Storage Services](#data-storage-services)
* [Resource Management](#resource-management)
* [Resource Monitoring](#resource-monitoring)
* [Resources/Articles](#resourcesarticles)


-  more than one solution for a task or application in GCP, a [solution continuum](https://github.com/Patechoc/GCP_memo/blob/master/cloud_architect/course_2_Essential_Cloud_Infrastructure__Foundation.md#gcp-infrastruture)
- Infrastructure, Users, Applications [analogy](https://github.com/Patechoc/GCP_memo/blob/master/cloud_architect/course_2_Essential_Cloud_Infrastructure__Foundation.md#gcp-infrastruture)

GCP offers a **range of Compute Services**

<img src="../images/core_services_Compute_Services.png"
        alt="core_services_Compute_Services.png"
        style="float: left; margin-right: 10px;" />


## Cloud Identity and Access Management (Cloud IAM)

- [Cloud IAM overview](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/UbUc3/cloud-iam)

Cloud IAM is a sophisticated system built on top of.

- email-like address names,
- job type roles in granular permissions.

Components within Cloud IAM which are **organizations**, **roles**, **members** and **service accounts**


[video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/UbUc3/cloud-iam) 

Who can do What on Which resources:

<img src="../images/core_services_Cloud_IAM_Who_DoWhat_WhichResource.png"
        alt="core_services_Cloud_IAM_Who_DoWhat_WhichResource.png"
        style="float: left; margin-right: 10px;" />


Cloud IAM objects: 

<img src="../images/core_services_Cloud_IAM_objects.png"
        alt="core_services_Cloud_IAM_objects.png"
        style="float: left; margin-right: 10px;" />


Cloud IAM resource hierarchy:

<img src="../images/core_services_Cloud_IAM_resource_hierarchy.png"
        alt="core_services_Cloud_IAM_resource_hierarchy.png"
        style="float: left; margin-right: 10px;" />

> Apply the **Principle of Least Priviledges**: Always select the smallest scope that's necessary for the task in order to reduce your exposure to risk!

### Organizations

[video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/M0m2G/organization)

- **"Organization Admin"**
- **"Project Creator"**

<img src="../images/core_services_Cloud_IAM_resource_Organization.png"
        alt="core_services_Cloud_IAM_resource_Organization.png"
        style="float: left; margin-right: 10px;" />

Responsabilities of:

- **"Cloud Identity account manager"**
- **"Organization Admin"**

<img src="../images/core_services_GCP_resources.png"
        alt="core_services_GCP_resources.png"
        style="float: left; margin-right: 10px;" />


### Folders: sub-organizations

Folders can act as a sub-organization wihtin the organization.

<img src="../images/core_services_Cloud_IAM_resource_Folders.png"
        alt="core_services_Cloud_IAM_resource_Folders.png"
        style="float: left; margin-right: 10px;" />

<img src="../images/core_services_Cloud_IAM_resource_every_Roles_of_a_project.png"
        alt="core_services_Cloud_IAM_resource_every_Roles_of_a_project.png"
        style="float: left; margin-right: 10px;" />


### Roles

[video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/rgNsR/roles)

= Roles define the can do what on which resource part of Cloud IAM


There are three types of roles in Cloud IAM; **Primitive roles**, **predefined roles**, and **custom roles**:

<img src="../images/core_services_Cloud_IAM_Roles.png"
        alt="core_services_Cloud_IAM_Roles.png"
        style="float: left; margin-right: 10px;" />

- **Primitive roles** are the original roles that were available in the GCP console, but they are broad. You apply them to a GCP project and they affect all resources in that project.

<img src="../images/core_services_Cloud_IAM_Roles_primitive.png"
        alt="core_services_Cloud_IAM_Roles_primitive.png"
        style="float: left; margin-right: 10px;" />

<img src="../images/core_services_Cloud_IAM_Roles_primitive_coarse_grained.png"
        alt="core_services_Cloud_IAM_Roles_primitive_coarse_grained.png"
        style="float: left; margin-right: 10px;" />

- **Predefined roles** define where those roles can be applied. This provides members with granular access to specific GCP resources and prevents unwanted access to other resources. These roles are collections of permissions because to do any meaningful operations, you usually need more than one permission.

<img src="../images/core_services_Cloud_IAM_Roles_predefined.png"
        alt="core_services_Cloud_IAM_Roles_predefined.png"
        style="float: left; margin-right: 10px;" />


<img src="../images/core_services_Cloud_IAM_Roles_predefined_ex.png"
        alt="core_services_Cloud_IAM_Roles_predefined_ex.png"
        style="float: left; margin-right: 10px;" />


<img src="../images/core_services_Cloud_IAM_Roles_predefined_all.png"
        alt="core_services_Cloud_IAM_Roles_predefined_all.png"
        style="float: left; margin-right: 10px;" />

But what if one of those roles does not have enough permissions or you need something even finer-grained?

That's what **Custom Roles** permit: a lot of companies use the **least privileged model** in which each person in your organization is given the minimal amount of privilege needed to do their job.

<img src="../images/core_services_Cloud_IAM_Roles_custom.png"
        alt="core_services_Cloud_IAM_Roles_custom.png"
        style="float: left; margin-right: 10px;" />

#### Demo: Create a Custom role in GCP

[video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/3bQES/demo-custom-roles)



### Members

[video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/4vrs0/members)

= **Members** define the who part, of who can do what, on which resource.

<img src="../images/core_services_Cloud_IAM_Members.png"
        alt="core_services_Cloud_IAM_Members.png"
        style="float: left; margin-right: 10px;" />




There are 5 different types of members:

- **Google Accounts**: a Google Account represents a developer, an administrator or any other person who interacts with GCP
- **Service Accounts**,
- **Google Groups**,
- **G Suite Domains**, and
- **Cloud Identity Domains**. 


 What if you already have a different corporate directory? How can you get your users and groups into GCP? 
 
Use **Google Cloud Directory Sync**!!

<img src="../images/core_services_Cloud_IAM_remote_LDAP_Members.png"
        alt="core_services_Cloud_IAM_remote_LDAP_Members.png"
        style="float: left; margin-right: 10px;" />


Many ways to sync your remote account:

<img src="../images/core_services_Cloud_IAM_remote_LDAP_Members_SSO.png"
        alt="core_services_Cloud_IAM_remote_LDAP_Members_SSO.png"
        style="float: left; margin-right: 10px;" />




### Service Accounts

[video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/292ex/service-accounts)


 A service account is an account that belongs to your application instead of to an individual end user

<img src="../images/core_services_Cloud_IAM_service_account_id.png"
        alt="core_services_Cloud_IAM_service_account_id.png"
        style="float: left; margin-right: 10px;" />

<img src="../images/core_services_Cloud_IAM_service_account_default_for_app_engine.png"
        alt="core_services_Cloud_IAM_service_account_default_for_app_engine.png"
        style="float: left; margin-right: 10px;" />

 
#### Scopes

<img src="../images/core_services_Cloud_IAM_service_account_scope.png"
        alt="core_services_Cloud_IAM_service_account_scope.png"
        style="float: left; margin-right: 10px;" />


<img src="../images/core_services_Cloud_IAM_user_created_service_accounts_only_predefined_roles.png"
        alt="core_services_Cloud_IAM_user_created_service_accounts_only_predefined_roles.png"
        style="float: left; margin-right: 10px;" />


Services Accounts use keys:

<img src="../images/core_services_Cloud_IAM_service_accounts_use_keys.png"
        alt="core_services_Cloud_IAM_service_accounts_use_keys.png"
        style="float: left; margin-right: 10px;" />

### Cloud IAM best practices

- [Module intro video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/xghL2/cloud-iam-best-practices)
- [Module Review video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/u8ETv/module-review)

<img src="../images/core_services_Cloud_IAM_best_practices_resource_hierarchy.png"
        alt="core_services_Cloud_IAM_best_practices_resource_hierarchy.png"
        style="float: left; margin-right: 10px;" />

Grant roles to groups instead of individuals:

<img src="../images/core_services_Cloud_IAM_best_practices_groups.png"
        alt="core_services_Cloud_IAM_best_practices_groups.png"
        style="float: left; margin-right: 10px;" />


Example of best practices when using Service Accounts:

<img src="../images/core_services_Cloud_IAM_best_practices_example_service_Accounts.png"
        alt="core_services_Cloud_IAM_best_practices_example_service_Accounts.png"
        style="float: left; margin-right: 10px;" />

#### Cloud IAP


Cloud IAP lets you establish a central authorization layer for applications accessed by HTTPS.
So you can use an application level access control model instead of relying on network level firewalls. Applications and resources protected by Cloud IAP can only be accessed through the proxy by users and groups with the correct Cloud IAM role. 


<img src="../images/core_services_Cloud_IAM_best_practices_Cloud_IAP.png"
        alt="core_services_Cloud_IAM_best_practices_Cloud_IAP.png"
        style="float: left; margin-right: 10px;" />

### Lab Intro: Cloud IAM

- [lab notes](../labs/lab_Cloud_IAM.md)
- [walkthrough video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/mpXBr/lab-review-cloud-iam)


## Data Storage Services

- [Module intro video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/HBW4r/module-overview)
- Module Review video


Google offers several storage services to choose from:









## Resource Management

= Manage and examine **Billing** of GCP resources


## Resource Monitoring

=  monitor GCP resources using **StackDriver**

## Resources/Articles