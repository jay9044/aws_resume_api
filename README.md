## Resume Architecture

```mermaid
[User] --HTTPS--> [Lambda Function URL] --Fetches and Displays--> [DynamoDB]
                         |
                         V
                  [DynamoDB Table]
                         |
                         V
                 [Terraform Script]
                         |
                         V
              [GitHub Actions Workflow]
```
<div>
  <p style={{ textAlign: 'center', marginTop: '10px' }}>AWS Textual Representation</p>
</div>

### Explanation:

1. **User**: Represents the end user or client.

2. **Lambda Function URL**: Exposes an HTTP endpoint that, when accessed, triggers the Lambda function.

3. **Lambda Function**: Fetches and displays the resume from the DynamoDB table. The function is deployed and accessible via the Lambda Function URL.

4. **DynamoDB**: Stores the resume data in JSON format.

5. **DynamoDB Table**: The actual DynamoDB table where resume data is stored.

6. **Terraform Script**: Defines the infrastructure as code (IaC) for provisioning the DynamoDB table and Lambda function.

7. **GitHub Actions Workflow**: A workflow that is triggered by events in the GitHub repository. It runs Terraform to provision and update the infrastructure when changes occur.
