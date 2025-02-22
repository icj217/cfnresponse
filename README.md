# cfnresponse

This package contains the Amazon Web Services (AWS) cfnresponse module which is
available in Python AWS Lambda environments.

The code for this module can be found [in the Lambda Function Code documentation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-lambda-function-code.html#cfn-lambda-function-code-cfnresponsemodule)
and in the [awslabs GitHub repo](https://github.com/awslabs/aws-cloudformation-templates/blob/master/aws/services/CloudFormation/MacrosExamples/StackMetrics/lambda/cfnresponse.py)

You can compare the code in `awslabs` with this pypi package with this command

```
if [ "$(curl -s https://raw.githubusercontent.com/awslabs/aws-cloudformation-templates/master/aws/services/CloudFormation/MacrosExamples/StackMetrics/lambda/cfnresponse.py | sha256sum)" = "$(curl -s https://raw.githubusercontent.com/gene1wood/cfnresponse/master/cfnresponse/__init__.py | sha256sum)" ]; then echo "GitHub matches AWS"; fi
if [ "$(curl -s https://raw.githubusercontent.com/awslabs/aws-cloudformation-templates/master/aws/services/CloudFormation/MacrosExamples/StackMetrics/lambda/cfnresponse.py | sha256sum)" = "$(wget --quiet https://files.pythonhosted.org/packages/03/69/2d3fafdf434a0d8ef62a5c1fa09feda25b31fad4db20c54ed067054f9b95/cfnresponse-1.1.2-py2.py3-none-any.whl && unzip -p cfnresponse-1.1.2-py2.py3-none-any.whl cfnresponse/__init__.py | sha256sum && rm cfnresponse-1.1.2-py2.py3-none-any.whl)" ]; then echo "Pypi matches AWS"; fi
```

This module [used to use the vendored version of `requests`](https://github.com/awslabs/aws-cloudformation-templates/blob/dd484dd32680fcbfc52b34de45923f78b5626e39/aws/services/CloudFormation/MacrosExamples/StackMetrics/lambda/cfnresponse.py)
provided by `botocore` but this changed in 
[April 2020](https://github.com/awslabs/aws-cloudformation-templates/commit/44b76a1f694f82eeee14fe804bf9dc973fdc2230#diff-f6c57142d56d8704aaf1d429ff1a06a6dd3f2ee6d80f0572ada8af010ff17124)
to instead use `urllib3` as
[`botocore.vendored.requests` was removed](https://github.com/boto/botocore/pull/1829).