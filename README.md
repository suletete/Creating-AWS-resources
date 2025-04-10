
### 1. **Setting Up the Environment**
   - **Environment Variables & Argument Check**: 
     - You began by accepting an argument to specify the environment (e.g., local, testing, or production).
     - A function (`check_num_of_args`) was created to verify if the correct number of arguments was passed. If not, it shows the usage and exits the script.
     - The `activate_infra_environment` function was designed to take the environment variable and output which environment the script will run for (local, testing, or production). It also handles invalid environment input.

### 2. **Checking Pre-requisites**
   - **Checking AWS CLI Installation**:
     - Before running AWS-related commands, you created a `check_aws_cli` function to verify whether the AWS CLI tool is installed on your machine. This ensures that you can interact with AWS resources programmatically.
   - **Checking AWS Profile**:
     - A `check_aws_profile` function was created to ensure that the `AWS_PROFILE` environment variable is set. This variable is needed for AWS CLI to authenticate and interact with your AWS account.

### 3. **Provisioning EC2 Instances**
   - **EC2 Instance Creation Function (`create_ec2_instances`)**:
     - In this function, you used the AWS CLI to provision EC2 instances with specific parameters.
     - The `instance_type`, `ami_id`, `count`, and `region` were stored in variables for easy customization.
     - The AWS CLI `aws ec2 run-instances` command was used to create the instances. It requires the AMI ID (Amazon Machine Image ID), instance type, count, and key pair for SSH access.
     - After the command, you used the `$?` variable to check if the command executed successfully. If the exit status is `0`, the script prints "EC2 instances created successfully." Otherwise, it prints an error message.

### 4. **Creating S3 Buckets with Arrays**
   - **Array of Departments**:
     - In the `create_s3_buckets` function, you used an array to store the names of various departments: Marketing, Sales, HR, Operations, and Media. Arrays are useful here because you need to create multiple S3 buckets with similar naming conventions.
   - **Looping through Array to Create S3 Buckets**:
     - You looped through each department name in the array and dynamically created a unique S3 bucket for each using the format: `company-department-Data-Bucket`.
     - The `aws s3api create-bucket` command was used to create each S3 bucket in the specified region.
     - Similar to EC2 instance creation, the `$?` variable was checked to determine if each bucket was created successfully. If the command was successful, it echoed that the bucket was created; otherwise, it displayed an error message.

### 5. **Combining the Functions**
   - **Final Script Structure**:
     - You combined all the individual functions into one comprehensive script.
     - The script first checks the number of arguments and sets the environment.
     - It then checks the prerequisites (AWS CLI installation and profile setup).
     - After passing the checks, it proceeds to create the EC2 instances and S3 buckets using the defined functions.
   - **Executing the Functions**:
     - Finally, you called each of the functions in sequence: `create_ec2_instances` and `create_s3_buckets`. These functions were executed one after the other to provision the resources in AWS.

### Key Concepts You Learned:
- **Functions in Shell Scripting**: You created reusable functions for specific tasks (EC2 provisioning and S3 bucket creation), making the script modular.
- **Arrays in Shell Scripting**: Arrays were used to manage multiple related data points (department names) efficiently.
- **AWS CLI Commands**: You learned how to interact with AWS resources programmatically using the `aws ec2` and `aws s3api` commands.
- **Exit Status Checking**: Using `$?` to check the success or failure of commands allowed you to handle errors and provide useful feedback.
- **Environment Variable Management**: Ensuring that necessary environment variables (such as AWS profiles) are set before proceeding with operations ensures a smoother experience and avoids errors.

### Conclusion:
This mini project helped you automate the creation of AWS resources using shell scripts. By using functions, arrays, and AWS CLI commands, you streamlined the process of provisioning EC2 instances and creating S3 buckets for different departments. This approach can be scaled and modified to suit various automation needs in AWS, making it a valuable skill in DevOps and cloud infrastructure management.
