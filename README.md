# Cloud Resume Challenge

My portfolio, hosted on AWS with a serverless visitor counter, built as a full cloud project.

**Live site:** https://d2yykngnx1qihy.cloudfront.net

## Architecture

```mermaid
flowchart LR
    V[Visitor browser] -->|1. load page| CF[CloudFront]
    CF --> S3[(S3 bucket<br/>private)]
    V -->|2. counter API call| L[Lambda<br/>Function URL]
    L --> D[(DynamoDB<br/>visitor count)]
```

## Deployment

```mermaid
flowchart LR
    P[git push to main] --> GA[GitHub Actions<br/>test, then deploy]
    GA -->|OIDC role| AWS[AWS]
    TF[Terraform] -->|builds stack| AWS
```

## Repositories

- [cloud-resume-frontend](https://github.com/prarthana2301/cloud-resume-frontend): this repo, the static site and its deploy pipeline
- [cloud-resume-backend](https://github.com/prarthana2301/cloud-resume-backend): Lambda code, pytest tests and deploy pipeline
- [cloud-resume-infra](https://github.com/prarthana2301/cloud-resume-infra): Terraform for the whole stack# cloud-resume-frontend