# quickstart-snyk-serverless
## Snyk Serverless CI/CD for the Enterprise on the AWS Cloud

This Quick Start enables you to use Snyk software as a service (SaaS) AWS integrations. It helps you secure your applications by finding, fixing, and monitoring potential vulnerabilities in open-source dependencies. With Snyk, you can build security into your continuous-development process. 

This reference deployment builds a continuous integration and continuous delivery (CI/CD) environment on the AWS Cloud. As a foundation, it uses the [Serverless CI/CD Quick Start created by Trek10](https://aws.amazon.com/quickstart/architecture/serverless-cicd-for-enterprise/). This CI/CD environment provides an enterprise-ready, dynamic deployment pipeline for your serverless applications. The Quick Start is automated by AWS CloudFormation templates that deploy a Snyk serverless integration in about 20 minutes in your AWS accounts.

Following AWS best practices for isolating resources, this Quick Start walks you through creating three AWS accounts (subaccounts): development, production, adn shared services. As shown in Figure 1, you deploy AWS Identity and Access Management (IAM) roles and policies into these accounts to grant your Snyk organization ID access to the Lambda resources in these accounts. (Depending on the workflow of your CI/CD pipeline, you may want to integrate additional services as well.) This cross-account access establishes integrations that secure your CI/CD pipeline so that you can use Snyk to perform security scans of your applications.

<p align="center">
    <img src="./images/Snyk-3-cross-acct-IAM-roles.png">
</p>
<p align="center">Figure 1: This Quick Start integrates Snyk with three AWS accounts</p> 

### Architecture

As shown in Figure 2, the Quick Start integrates your Lambda functions into your Snyk organization. In addition, using the Trek10 Quick Start as a submodule, it automatically sets up a serverless CI/CD environment. For details on the resources deployed, read the [Trek10 Serverless CI/CD Quick Start deployment guide](https://fwd.aws/53avp).

<p align="center">
    <img src="./images/Snyk-arch-diagram.png">
</p>
<p align="center">Figure 2: Quick Start architecture for Snyk serverless CI/CD on AWS</p>

### Prepare your AWS account

1. Sign in to your AWS account at [https://aws.amazon.com](https://aws.amazon.com/) with an IAM user role that has the necessary permissions. 
2. Set up subaccounts for shared services, development, and production: 
    1. Open the AWS Organizations console at [https://console.aws.amazon.com/organizations/](https://console.aws.amazon.com/organizations/). Follow the instructions in the AWS documentation to [create an organization](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_create.html).
    2. Follow the instructions in the AWS documentation to [create three subaccounts](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_accounts_create.html): shared services, development, and production. If you have a large development organization, consider creating separate sets of these three subaccounts for each business unit or logical grouping of applications.
    3. Save the AWS account IDs for all three subaccounts (shared services, development, and production). You will use these in a later step. For additional information, see [Finding your AWS account ID in the AWS documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/console_account-alias.html).

### Get your Snyk organization ID

This Quick Start requires that you have a Snyk login or subscription. If you don't have a Snyk login, open the page for the [Snyk: Developer-First Security](https://aws.amazon.com/marketplace/pp/B085VGM85Q?qid=1587078167615&sr=0-1&ref_=srh_res_product_title) in AWS Marketplace, and choose **Continue to Subscribe.** Review the terms and conditions for software usage, and choose **Accept Terms**. A confirmation page loads, and an email confirmation is sent to the account owner. For detailed subscription instructions, see the [AWS Marketplace documentation](https://aws.amazon.com/marketplace/help/200799470).

1. Sign in to your [Snyk account](https://snyk.io/). 
2. Select the **Settings** tab. Under **Organization ID**, choose **Copy**. Save this ID. You will use it in a later step.

### Enable cross-account access

#### In the development subaccount:

1. Sign in to the development subaccount as a user with IAM permission to create a CloudFormation stack and deploy IAM roles.
2. [Deploy a Trek10 IAM role](https://fwd.aws/YrVVz).
3. [Deploy a Snyk IAM role](https://fwd.aws/d9KN5).
4. Sign out of the development subaccount.

#### In the production subaccount:

1. Sign in to the production subaccount as a user with IAM permission to create a CloudFormation stack and deploy IAM roles. 
2. [Deploy a Trek10 IAM role](https://fwd.aws/YrVVz).
3. [Deploy a Snyk IAM role](https://fwd.aws/d9KN5).
4. Sign out of the production subaccount.

### Deploy resources
1. Sign in to the AWS shared services subaccount as a user with IAM permissions to create resources in several AWS services. We recommend using the **AdministratorAccess** managed policy.
2. [Deploy resources across the three subaccounts](https://fwd.aws/YeDwE).


To post feedback, submit feature ideas, or report bugs, use the **Issues** section of this GitHub repo.
If you'd like to submit code for this Quick Start, please review the [AWS Quick Start Contributor's Kit](https://aws-quickstart.github.io/).
