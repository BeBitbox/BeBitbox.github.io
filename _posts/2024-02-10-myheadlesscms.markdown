---
layout: post
title:  Building My Efficient Headless CMS
date:   2024-02-10 15:21:57 +0100
permalink: /my-headless-cms/
---

## Introduction

The quest for the most efficient method to host simple websites, such as a local hairdresser's page, is a topic I often ponder.
These websites require infrequent updates, maybe just a change in operating hours or the addition of new photographs.
Despite this, many developers opt for comprehensive Content Management Systems (CMS) like WordPress or Drupal.
Such platforms offer extensive features, including user and content management, which are largely underutilized for sites with sporadic content updates.
Moreover, these solutions necessitate a continuously running database, awaiting visitors.
This approach, in my view, represents an inefficient use of resources, prompting me to advocate for the adoption of a headless CMS.

## The architecture
![Architecture](/images/my-headless-cms.png)

## The Shift to Headless CMS
In this post, I'll detail my chosen architecture implementing a headless CMS solution, diverging from traditional practices.
Unlike standard CMS platforms that provide RESTful APIs, my approach involves generating static JSON files.
This method significantly simplifies content delivery, reducing the demand on server resources and enhancing site performance.

### Key Advantages
- **Reduced Complexity:** By eliminating unnecessary features and focusing on core functionalities, we streamline operations and lower the potential for technical issues.
- **Enhanced Performance:** The absence of a database reduces server load, potentially improving page load times and overall website speed.
- **Simplified Management:** With static JSON files, content management becomes more straightforward, facilitating easier updates and maintenance.
- **No locking:** There is no vendor-locking or data-locking. Everything is under our control and license free.
- **Cost:** Where some traditional CMS have hosting bills around 100 - 200€, my hosting cost for a new website is about 20€.

### Limitations
This headless CMS has a focus on small businesses or projects, but not web shops or advanced websites because of the following limitations:
- **Mainly public data:** This setup is for simple websites that require no private or restricted data.
- **Structural changes:** If a client wants a new page or new content, then that structural change will require the involvement of a developer.

### Implementation Overview
#### AWS Route53
This DNS component will provide a hosted zone with all the necessary records and redirecting.
The domain name for the website and CMS are registered here, for about 9€/year.
The cost of a hosted zone is about 6€/year.

#### AWS CloudFront
CloudFront acts like a CDN (Content Delivery Network), but I mainly use it for the HTTPS offloading with a certificate managed in the AWS Certificate Manager.
This component is configured to redirect HTTPS to the HTTP-address of the S3 bucket.

#### AWS S3
I've activated the static website hosting feature of the S3 bucket, so it will serve all the necessary files including HTML, CSS, JavaScript, images and even data in the form of JSON-files.
Everything on this bucket can be publicly read and only the CMS has the authorization to update or delete.
The monthly cost of this hosting is about 2 cent per month with a normal load.
For scenarios anticipating higher traffic, we can activate the caching features on CloudFront.

#### AWS Lambda
If I want to handle some website generated events or the submitting of a form, I'll deploy a specific AWS Lambda's to handle the task.
The cost of this depends on the number of invocations and the action, so it is also very scalable.

#### AWS Load Balancer + EC2
The most significant expense in this setup arises from maintaining the CMS operational.
To achieve this, I've deployed an EC2 instance, which incurs an annual cost of around 100€. 
I use an application load balancer for HTTPS offloading and for directing requests to the appropriate instance where the CMS is hosted.

Access to the CMS is safeguarded by integration with an OpenID provider, such as Google or Microsoft, ensuring that authentication is both secure and user-friendly.
Permissions are dynamically assigned based on the user's email address, granting appropriate rights to modify website content, including images and data.
Update a text for example will update a JSON file on the designated S3 bucket, ensuring the client website shows immediately the latest content.

## Conclusion
Adopting a headless CMS for simple websites not only aligns with the principles of efficiency and simplicity but also opens new possibilities for web development. 
By focusing on what truly matters - delivering content in the most direct and uncomplicated manner - we can create faster, more reliable, and cheaper websites.
Stay tuned for further updates as I delve deeper into this venture, sharing insights and learnings along the way.