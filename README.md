# AWS CI/CD Project

A continuous integration and continuous deployment (CI/CD) pipeline implementation using AWS services.

## Overview

This project demonstrates how to set up and manage a complete CI/CD pipeline using various AWS services to automate the build, test, and deployment processes for applications.

## Architecture

The CI/CD pipeline leverages the following AWS services:

- **AWS CodeCommit** - Source control repository
- **AWS CodeBuild** - Build and test automation
- **AWS CodeDeploy** - Application deployment
- **AWS CodePipeline** - Pipeline orchestration
- **Amazon S3** - Artifact storage
- **AWS CloudFormation** - Infrastructure as Code
- **AWS IAM** - Access management

## Prerequisites

Before getting started, ensure you have:

- AWS CLI installed and configured
- AWS account with appropriate permissions
- Basic understanding of AWS services
- Git installed on your local machine

## Getting Started

### 1. Clone the Repository

```bash
git clone <repository-url>
cd aws-cicd
```

### 2. Configure AWS CLI

```bash
aws configure
```

Enter your AWS Access Key ID, Secret Access Key, default region, and output format.

### 3. Set Up Environment Variables

Create a `.env` file in the project root:

```bash
AWS_REGION=us-east-1
AWS_ACCOUNT_ID=your-account-id
PROJECT_NAME=aws-cicd-demo
```

## Project Structure

```
aws-cicd/
├── README.md
├── .gitignore
├── buildspec.yml          # CodeBuild configuration
├── appspec.yml           # CodeDeploy configuration
├── cloudformation/       # CloudFormation templates
│   ├── pipeline.yml
│   ├── infrastructure.yml
│   └── iam-roles.yml
├── scripts/              # Deployment scripts
│   ├── deploy.sh
│   └── cleanup.sh
├── src/                  # Application source code
└── tests/                # Test files
```

## Pipeline Stages

1. **Source Stage**: Triggers on code commits to the main branch
2. **Build Stage**: Compiles code, runs tests, and creates artifacts
3. **Deploy Stage**: Deploys application to target environment

## Configuration Files

### buildspec.yml
Defines the build commands and phases for CodeBuild.

### appspec.yml
Specifies deployment instructions for CodeDeploy.

### CloudFormation Templates
Infrastructure as Code templates for creating AWS resources.

## Deployment

### Manual Deployment

```bash
# Deploy infrastructure
aws cloudformation deploy --template-file cloudformation/infrastructure.yml --stack-name aws-cicd-infra

# Deploy pipeline
aws cloudformation deploy --template-file cloudformation/pipeline.yml --stack-name aws-cicd-pipeline
```

### Automated Deployment

The pipeline automatically triggers on code changes to the main branch.

## Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `AWS_REGION` | AWS region for resources | `us-east-1` |
| `AWS_ACCOUNT_ID` | AWS account identifier | - |
| `PROJECT_NAME` | Project name prefix | `aws-cicd` |

## Monitoring and Logging

- **CloudWatch Logs**: Build and deployment logs
- **CloudWatch Metrics**: Pipeline performance metrics
- **AWS X-Ray**: Application tracing (if enabled)

## Security Best Practices

- Use IAM roles with least privilege access
- Enable CloudTrail for audit logging
- Encrypt artifacts in S3
- Use AWS Secrets Manager for sensitive data
- Enable VPC endpoints for private communication

## Troubleshooting

### Common Issues

1. **Build Failures**
   - Check CloudWatch logs in CodeBuild
   - Verify buildspec.yml syntax
   - Ensure proper IAM permissions

2. **Deployment Failures**
   - Review CodeDeploy logs
   - Check appspec.yml configuration
   - Verify target environment health

3. **Pipeline Issues**
   - Check CodePipeline execution history
   - Verify source repository permissions
   - Review artifact configurations

## Cost Optimization

- Use appropriate instance types for builds
- Implement lifecycle policies for S3 artifacts
- Monitor and optimize resource usage
- Use AWS Cost Explorer for cost analysis

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

For questions and support:
- Create an issue in the repository
- Check AWS documentation
- Review CloudFormation templates

## Resources

- [AWS CodePipeline Documentation](https://docs.aws.amazon.com/codepipeline/)
- [AWS CodeBuild Documentation](https://docs.aws.amazon.com/codebuild/)
- [AWS CodeDeploy Documentation](https://docs.aws.amazon.com/codedeploy/)
- [AWS CloudFormation Documentation](https://docs.aws.amazon.com/cloudformation/)

---

**Note**: This README will be updated as the project evolves. Please refer to the latest version for current information.
