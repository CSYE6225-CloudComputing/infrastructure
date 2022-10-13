# infrastructure

We are going to start setting up our AWS infrastructure. This assignment will focus on setting up our networking resources such as Virtual Private Cloud (VPC), Internet Gateway, Route Tables, and Routes. We will use AWS CloudFormation for infrastructure setup and tear down.

# Installation

From the CLI:

IF you have the AWS CLI installed, and IF you have already configured it with your access key and secret key (any region), and IF your command prompt is located in the same directory as your YML file, you can run this command:

```aws --profile=dev cloudformation create-stack --stack-name csye6225-infra --template-body file://csye6225-infra.yml```

--stack-name: Can be anything you like, but I'll refer to "csye6225-infra" throughout the article.

--template-body: The file you have been working on.

If you have any syntactical errors, they will be presented back to you immediately. Fix these before proceeding. Typically errors result from use of tabs instead of spaces, spaces in unusual places, = instead of :, or special characters embedded by the editor you are using.

However not all can be discovered by CloudFormation right away. You could encounter a non-syntactical error (e.g. permissions) several minutes into a stack creation. When this happens, you'll have to check the status periodically to detect issues. A convenient alternative is to wait for the stack to finish, or error out, with this function:

```aws --profile=dev cloudformation wait stack-create-complete --stack-name csye6225-infra ```

...and when the stack is complete you can use the following to examine it:

```aws --profile=dev cloudformation describe-stacks```

From the CLI update the stack using this command:

```aws --profile=dev cloudformation update-stack --stack-name csye6225-infra --template-body file://csye6225-infra.yml```

And as before, you can use the wait command to monitor progress:

```aws --profile=dev cloudformation wait stack-update-complete --stack-name csye6225-infra```


# Deleting Stack

One cloud-native concept to get comfortable with is that Resources are Disposable. We can create and delete the stack whenever we wish now that we have our template.

From the console, select the stack and take the 'delete stack' action. Or from the CLI run command

``` aws --profile=dev cloudformation delete-stack --stack-name csye6225-infra```