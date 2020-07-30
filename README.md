# quickstart-snyk-serverless
## Snyk Serverless CI/CD for the Enterprise on the AWS Cloud

This Quick Start enables you to use Snyk software as a service (SaaS) Amazon Web Services (AWS) integrations. It helps you secure your applications by finding, fixing, and monitoring potential vulnerabilities in open-source dependencies. With Snyk, you can build security into your continuous-development process.  

This reference deployment builds a continuous integration and continuous delivery (CI/CD) environment on the AWS Cloud. As a foundation, it uses the [Serverless CI/CD Quick Start created by Trek10](https://fwd.aws/jXjN8). This CI/CD environment provides an enterprise-ready, dynamic deployment pipeline for your serverless applications.

Following AWS best practices for isolating resources, this Quick Start walks you through creating three AWS accounts (subaccounts): development, production, and shared services. You deploy AWS Identity and Access Management (IAM) roles and policies into these accounts to grant your Snyk organization access to the AWS Lambda resources in these accounts. (Depending on the workflow of your CI/CD pipeline, you may want to integrate additional services as well.) This cross-account access establishes integrations that secure your CI/CD pipeline so that you can use Snyk to perform security scans of your applications.

As shown in Figure 1, you deploy IAM roles into your development, production, and shared services accounts. These roles grant your Snyk organization ID access to your Lambda resources.

<p align="center">
    <img src="./images/Snyk-3-cross-acct-IAM-roles.png">
</p>
<p align="center">Figure 1: AWS accounts integrated with Snyk</p> 

As shown in Figure 2, the Quick Start integrates your Lambda functions into your Snyk organization. In addition, using the Trek10 Quick Start as a submodule, it automatically sets up a serverless CI/CD environment. 

<p align="center">
    <img src="./images/Snyk-arch-diagram.png">
</p>
<p align="center">Figure 2: Quick Start architecture for Snyk serverless CI/CD on AWS</p>

For details on the resources deployed, read the [Trek10 Serverless CI/CD Quick Start deployment guide](https://fwd.aws/53avp). For step-by-step instructions and customization options for this Quick Start, see the [Snyk Serverless CI/CD Quick Start deployment guide](https://fwd.aws/mrrMK).

To post feedback, submit feature ideas, or report bugs, use the **Issues** section of this GitHub repo.

If you'd like to submit code for this Quick Start, please review the [AWS Quick Start Contributor's Kit](https://aws-quickstart.github.io/).
