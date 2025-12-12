
## Deployment Steps

1. Clone this repository to your local machine.

2. Navigate to the project Stack 1. This stack includes VPC, Aurora servlerless and S3

3. Initialize Terraform:
   ```
   terraform init
   ```

4. Review and modify the Terraform variables in `main.tf` as needed, particularly:
   - AWS region
   - VPC CIDR block
   - Aurora Serverless configuration
   - s3 bucket

5. Deploy the infrastructure:
   ```
   terraform apply
   ```
   Review the planned changes and type "yes" to confirm.

6. After the Terraform deployment is complete, note the outputs, particularly the Aurora cluster endpoint.

7. Prepare the Aurora Postgres database. This is done by running the sql queries in the script/ folder. This can be done through Amazon RDS console and the Query Editor.

8. Navigate to the project Stack 2. This stack includes Bedrock Knowledgebase

9. Initialize Terraform:
   ```
   terraform init
   ```

10. Use the values outputs of the stack 1 to modify the values in `main.tf` as needed:
     - Bedrock Knowledgebase configuration

11. Deploy the infrastructure:
      ```
      terraform apply
      ```
      - Review the planned changes and type "yes" to confirm.


12. Upload pdf files to S3, place your files in the `spec-sheets` folder and run:
      ```
      python scripts/upload_to_s3.py
      ```
      - Make sure to update the S3 bucket name in the script before running.

13. Sync the data source in the knowledgebase to make it available to the LLM.

## Using the Scripts

### S3 Upload Script

The `upload_to_s3.py` script does the following:
- Uploads all files from the `spec-sheets` folder to a specified S3 bucket
- Maintains the folder structure in S3

To use it:
1. Update the `bucket_name` variable in the script with your S3 bucket name.
2. Optionally, update the `prefix` variable if you want to upload to a specific path in the bucket.
3. Run `python scripts/upload_to_s3.py`.

## Complete chat app

### Complete invoke model and knoweldge base code
- Open the bedrock_utils.py file and the following functions:
  - query_knowledge_base
  - generate_response

### Complete the prompt validation function
- Open the bedrock_utils.py file and the following function:
  - valid_prompt

  Hint: categorize the user prompt

## Troubleshooting

- If you encounter permissions issues, ensure your AWS credentials have the necessary permissions for creating all the resources.
- For database connection issues, check that the security group allows incoming connections on port 5432 from your IP address.
- If S3 uploads fail, verify that your AWS credentials have permission to write to the specified bucket.
- For any Terraform errors, ensure you're using a compatible version and that all module sources are correctly specified.

For more detailed troubleshooting, refer to the error messages and logs provided by Terraform and the Python scripts.
