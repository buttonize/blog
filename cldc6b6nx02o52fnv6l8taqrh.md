# Why AWS Console desperately needs a competition?

The [motto](https://aws.amazon.com/console/) of AWS Console is loud and clear.

![AWS Console meme 1](https://cdn.hashnode.com/res/hashnode/image/upload/v1674681793674/GUvc-qsaX.jpeg align="left")

Which requires AWS to build a monstrous web app which must cover thousands of use-cases of their 150+ cloud services and to be honest – they are really trying do their best.

## What's the problem

The main advantage of AWS Console is at the same time its biggest problem – **it must cover everything** – from EC2 subnets management through Lambda code editor to IoT debugging tools.

![AWS Console meme 2](https://cdn.hashnode.com/res/hashnode/image/upload/v1674681795276/NURwHahM_.jpeg align="left")

Creating a UI which must cover so many completely different and abstract use-cases is a huge challenge and requires doing a ton of trade-offs which usually hurt the end user.

## AWS Console is meant for DevOps teams

AWS Console is mainly targeted on DevOps experts and developers trying new AWS services and by visually representing a cloud service, AWS makes it look more understandable and less scary - as sometimes more complex services can look like.

> **The reason why AWS Console is covering almost all the use-cases is because it's part of the sales process.**

![AWS Console meme 3](https://cdn.hashnode.com/res/hashnode/image/upload/v1674681796901/NdT3O6WJD.png align="left")

When a DevOps team accepts to use the service they switch to some scalable Infrastructure as Code solution anyway and they get back to the Management Console only in case of some IaC disaster or when they need to discover some new features of the service.

## New trends. New needs. New opportunities.

AWS Console showed us over the years that managed cloud services can have a simple but powerful user interface, through which we can build and manage big applications.

With rise of Serverless architecture the transition towards managed services is accelerating more and more and it brings many new challenges and opportunities.

> **That's where the new opportunities come into play – creating cloud consoles tailor made for given set of use-cases on top of AWS API.**

![Opportunity meme](https://cdn.hashnode.com/res/hashnode/image/upload/v1674681798494/UnDu5Fb6Dr.png align="left")

## AWS Console for non-technical teams

One of the main advantages of Serverless architecture is speed of development. Creating an API endpoint which can handle tens of thousands of requests per second is just a matter of couple clicks in AWS console or lines in IaC definition files.

Since developers are becoming more and more of a precious resource, companies want them to really focus on developing things which bring the biggest business added value.

### Busy developers

After releasing the app developers suddenly need to start dealing with the operations perspective of the business. They need to change system configurations based on product decisions every now and then. They are required to change some values inside a database for a certain user because of the sales team special deals and the list goes on – and during all this, they need to continue with fixing the bugs and developing new features.

> **So they either burn out quickly or they need to slow down in order to handle all the load.**

![Frontend Backend meme](https://cdn.hashnode.com/res/hashnode/image/upload/v1674681800581/i9ihO1YVH.png align="left")

### Non-technical teams coming to the rescue

The problem of developers shortage is being addressed by Low-code/No-code tools which help developers to offload some of the workload to non-technical team members.

Since only some of AWS use-cases would fit such a transition, it doesn't make sense to give those team members access to AWS Console directly, because they would get lost inside such a monstrous system – and they would see so many "Access Denied" error messages along the way.

**Solution could be a SaaS**. Which would handle all the important stuff like authentication, authorization, access auditing and it would provide a simple UI for those use-cases and also an easy way for developers to integrate it into their existing platform.

![SaaS meme](https://cdn.hashnode.com/res/hashnode/image/upload/v1674681802584/3xtyunz0A.png align="left")

### Example – Cognito

#### Problem

Support team needs to reset user's Cognito MFA settings because he lost his phone with the authenticator app and didn't backup his restoration codes.

#### Solution

Support team member goes to the SaaS, opens control panel called "User account" and sees there an input with button called "Reset MFA". He fills a "User ID" to the input field and clicks on the button.

![App Screenshot](https://cdn.hashnode.com/res/hashnode/image/upload/v1674681804028/0HeYxAvfv.png align="left")

#### Implementation

Developer opens the SaaS, enters "User Account" control panel and clicks on "Add new widget". Inside the wizard he adds "User ID" as required input parameter, then he selects that he would like the widget to call Cognito and selects the appropriate action, then he links the "User ID" input parameter to `username` attribute in Cognito API call and saves the widget.

Abstract example of the widget's AWS configuration:

```javascript
// Velocity VTL template
{
  "region": "eu-central-1",
  "service": "CognitoIdentityServiceProvider",
  "method": "adminSetUserMFAPreference",
  "params": {
    "UserPoolId": "eu-central-1_x1X1Ock9c",
    "Username": "$attributes.userId", // "User ID" input value
    "SoftwareTokenMfaSettings": {
      "Enabled": false,
      "PreferredMfa": false
    }
  }
}
```

## Serverless native

A big advantage of such tools would be that it is "Serverless native". Meaning that it would support the same way of thinking that the Serverless developers already have. I would support triggers for validating or modifying the data. I would support [AWS Service Integration Pattern](https://docs.aws.amazon.com/step-functions/latest/dg/connect-to-resource.html) to empower developers with the power of whole AWS cloud. I would support integration to CloudFormation through Custom Resources. And the list goes on.

![Serverless meme](https://cdn.hashnode.com/res/hashnode/image/upload/v1674681805878/JLv5zZYzM.png align="left")

## Conclusion

In upcoming years the community will see a lot of innovations coming up in the Serverless space. Since me and my team have 5+ years of experience with developing and operating Serverless applications, we see many opportunities in the space and creating such competitor for AWS console is one of them – and we definitely don't want to miss out on this one.

Make sure to follow me on Twitter [@FilipPyrek](https://twitter.com/FilipPyrek) to keep up-to-date with the latest Serverless news and let me know in the comments what you think about this idea.

%[https://twitter.com/filippyrek/status/1453034585659527169]