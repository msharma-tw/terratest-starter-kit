# Testing Infrastructure Code with GitHub Actions and Terratest

This repository is an example of testing IaC libraries written with [Terraform](https://terraform.io) using
[GitHub Actions](https://github.com/features/actions). 


## Prerequisites

To successfully run all the examples, you need the following tools:

* Repository in [GitHub](https://github.com) with the ability to run [GitHub Actions](https://github.com/features/actions)
* [Terraform, v0.12.20+](https://terraform.io), a tool for building, changing, and versioning infrastructure safely and efficiently.
* [Terratest](https://terratest.gruntwork.io/), a Go library that provides patterns and helper functions for testing infrastructure. Will be installed as a Go Library.
* [Go, v1.13+](https://golang.org/) binary in your PATH.
* [AWS Account](https://aws.amazon.com/) and [credentials for Terraform](https://www.terraform.io/docs/providers/aws/index.html#authentication)


## Running the tests

Note that to run the tests, you will have to have AWS Credentials available for Terraform.

### Unit tests

As the unit tests don't create any resources, they're safe to run as is. Check out the [terratest unit
test file](./test/terraform_aws_hello_world_unit_test.go) for details.

To run the unit tests, go to the `test` directory and run `go test -v ./Terraform_AWS/test -tags=unit`. 

### Integration tests

Integration test creates actual resources in AWS, so you will first have to set up your AWS Credentials.
Once that's done, you can run `go test -v ./Terraform_AWS/test -tags=integration`. Check out the [terratest integration test file](./test/terraform_aws_hello_world_integration_test.go) 
for details.
<!-- 
### Prettier test output

Go test output can sometimes be hard to read. A good tool to get human readable output is [`gotestsum`](https://github.com/gotestyourself/gotestsum).
Instead of the very verbose output, you get something like this: -->

```shell script
❯ go test -v ./Terraform_AWS/test -tags=unit
--- PASS: TestTerraformHelloWorldExample (0.42s)
PASS
ok      test/Terraform_Hello_World      0.437s
```

## Useful links

### Tools used in this repository

* https://terratest.gruntwork.io/
* https://www.terraform.io/
* https://help.github.com/en/actions

### Developing Modules and Infrastructure as Code

* https://www.terraform.io/docs/modules/index.html
* https://www.terraform.io/docs/modules/composition.html
* https://blog.gruntwork.io/how-to-create-reusable-infrastructure-with-terraform-modules-25526d65f73d
* https://blog.gruntwork.io/5-lessons-learned-from-writing-over-300-000-lines-of-infrastructure-code-36ba7fadeac1

### GitHub Actions for installing Terraform and Terragrunt

* https://github.com/

### Other utilities

* https://github.com/gotestyourself/gotestsum


```

go test -v ./Terraform_AWS/test/terraform_aws_hello_world_test.go -timeout 30m | tee Terraform_AWS/reports/test_output.log
terratest_log_parser -testlog test_output.log -outputdir test_output

```