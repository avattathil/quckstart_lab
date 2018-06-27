# Setting up your AWS enviornment

## Installing the AWS Command Line Interface
https://docs.aws.amazon.com/cli/latest/userguide/installing.html

## Install the AWS CLI Using the Bundled Installer (Linux, macOS, or Unix)
https://docs.aws.amazon.com/cli/latest/userguide/awscli-install-bundle.html

## Configuring the AWS CLI
https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html#cli-quick-configuration

## Test you configuration
` #aws s3 ls`
```
2016-11-10 20:28:19 cf-templates-1cgvn8v7ihvbt-ap-northeast-2
2016-11-10 20:29:47 cf-templates-1cgvn8v7ihvbt-ap-south-1
2016-11-10 20:28:43 cf-templates-1cgvn8v7ihvbt-ap-southeast-1
2016-11-10 20:29:03 cf-templates-1cgvn8v7ihvbt-ap-southeast-2
2016-11-10 20:26:47 cf-templates-1cgvn8v7ihvbt-eu-central-1
2016-11-10 20:25:47 cf-templates-1cgvn8v7ihvbt-eu-west-1
2017-01-25 15:11:23 cf-templates-1cgvn8v7ihvbt-eu-west-2
2016-11-10 20:30:12 cf-templates-1cgvn8v7ihvbt-sa-east-1
2016-03-30 11:16:46 cf-templates-1cgvn8v7ihvbt-us-east-1
2016-11-10 20:24:30 cf-templates-1cgvn8v7ihvbt-us-east-2
2016-03-23 19:25:57 cf-templates-1cgvn8v7ihvbt-us-west-1
2016-04-06 21:06:00 cf-templates-1cgvn8v7ihvbt-us-west-2
```

# Sample cfn-project
Download this tar https://s3.amazonaws.com/tonynv/sample-taskcat-project.tar

`wget https://s3.amazonaws.com/tonynv/sample-taskcat-project.tar`

# Untar files
`tar -xvf sample-taskcat-project.tar`
```
x sample-taskcat-project/
x sample-taskcat-project/ci/
x sample-taskcat-project/scripts/
x sample-taskcat-project/templates/
x sample-taskcat-project/templates/debug-yaml.template
x sample-taskcat-project/templates/debug.template
x sample-taskcat-project/scripts/scripts_userdata.sh
x sample-taskcat-project/ci/debug-input.json
x sample-taskcat-project/ci/taskcat-autobucket.yml
x sample-taskcat-project/ci/taskcat.yml
```
# Deploy the cfn
`taskcat -c sample-taskcat-project/ci/taskcat-autobucket.yml -m -p -n`
