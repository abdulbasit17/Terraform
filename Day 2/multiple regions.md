Multi-Region Implementation in Terraform


# Define the AWS provider for the us-east-1 region
provider "aws" {
  alias  = "us-east-1"
  region = "us-east-1"
}

# Define the AWS provider for the us-west-2 region
provider "aws" {
  alias  = "us-west-2"
  region = "us-west-2"
}

# Create an EC2 instance in the us-east-1 region
resource "aws_instance" "example" {
  ami           = "ami-0123456789abcdef0"  # Replace with a valid AMI ID for us-east-1
  instance_type = "t2.micro"
  provider      = aws.us-east-1
}

# Create an EC2 instance in the us-west-2 region
resource "aws_instance" "example2" {
  ami           = "ami-0123456789abcdef0"  # Replace with a valid AMI ID for us-west-2
  instance_type = "t2.micro"
  provider      = aws.us-west-2
}
Explanation:
Provider Definitions: Each provider block defines an AWS provider with an alias and a region. The alias allows you to refer to specific provider configurations in your resource definitions.
Resource Definition: In each resource block, you specify the provider using the alias you defined. This determines which AWS region the resource will be created in.
By using this approach, you can manage resources across different regions in a single Terraform configuration.






