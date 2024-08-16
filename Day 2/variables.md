Variables in Terraform
In Terraform, input and output variables are crucial for creating flexible, reusable, and dynamic configurations. They enable you to pass values into your modules and configurations and share values across different parts of your infrastructure.

Input Variables
Input variables allow you to parameterize your Terraform configurations. They enable you to provide values from outside your modules or configurations, making them more adaptable. Here's how to define an input variable:

hcl
Copy code
variable "example_var" {
  description = "An example input variable"
  type        = string
  default     = "default_value"
}
variable: Declares an input variable named example_var.
description: Provides a human-readable explanation of the variable's purpose.
type: Specifies the variable's data type (e.g., string, number, list, map, etc.).
default: Sets an optional default value for the variable.
You can use the input variable within your resource configurations like this:

hcl
Copy code
resource "example_resource" "example" {
  name = var.example_var
  # other resource configurations
}
Here, var.example_var references the input variable within the resource configuration.

Output Variables
Output variables are used to expose values from your module or configuration, making them available for use in other parts of your Terraform setup. Here's how to define an output variable:


output "example_output" {
  description = "An example output variable"
  value       = resource.example_resource.example.id
}
output: Declares an output variable named example_output.
description: Provides a description of the output variable.
value: Specifies the value to expose, which can be an attribute of a resource, a computed value, or any expression.
To reference output variables from other modules, use the syntax module.module_name.output_name, where module_name is the name of the module containing the output variable.

For example, if you have an output variable named example_output in a module called example_module, you can access it in the root module like this:


output "root_output" {
  value = module.example_module.example_output
}
This setup facilitates sharing data and values between different parts of your Terraform configuration, promoting a modular and maintainable infrastructure-as-code approach.