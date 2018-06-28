# Setting up your AWS enviornment

## Installing the AWS Command Line Interface (if not installed)
https://docs.aws.amazon.com/cli/latest/userguide/installing.html

## Install the AWS CLI Using the Bundled Installer (Linux, macOS, or Unix)
https://docs.aws.amazon.com/cli/latest/userguide/awscli-install-bundle.html

## Configuring the AWS CLI (if no default profile is configured)
https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html#cli-quick-configuration

## Test your configuration (do a simple command)
` #aws s3 ls`

> Should return something similar if you have your default profile set

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

# Install TaskCat

## Installing TaskCat (Docker install)

Prerequisites: Python 3.5+ and pip3

`pip3 install taskcat`

Installing via pip3 --user (for those who want to install taskcat into their homedir)

Prerequisites: Python 3.5+ and pip3 Note: (the user install dir is platform specific)

>For Example: (On Mac: ~/Library/Python/3.x/bin/taskcat)

>For Example: (On Linux: ~/.local/bin)

`pip3 install taskcat --user`

> WARNING: Be sure to add the python bin dir to your $PATH

## Docker based install

> WARNING: Only use this method if you have docker instaled
Prerequisites: `docker`

curl -s https://raw.githubusercontent.com/aws-quickstart/taskcat/master/installer/docker-install-master| sudo python -E

> Note: If you do not have root privileges Taskcat will install in the current directory
> Installing via pip3 (for those who do not want to use the docker installer)

## Cloudformation based install

If you are using a Windows workstation use the ec2 template: 

Download this template https://raw.githubusercontent.com/aws-quickstart/taskcat/master/installer/ec2/templates/taskcat.template and launch it.

Connect via ssh to the instance as ec2-user. 

> Note: You will need to create a role 

# Check taskcat is installation (run taskcat)
`taskcat`
> This should return the useage/help message


# Deploy the sample cfn
`taskcat -c sample-taskcat-project/ci/taskcat-autobucket.yml -m -p -n`

### Sample Output:
```
 _            _             _
| |_ __ _ ___| | _____ __ _| |_
| __/ _` / __| |/ / __/ _` | __|
| || (_| \__ \   < (_| (_| | |_
 \__\__,_|___/_|\_\___\__,_|\__|

version 2018.627.21629

[taskcat] :AWS AccountNumber: 	 [536065598225]
[taskcat] :Authenticated via: 	 [environment]

[taskcat] :Reading Config form: sample-taskcat-project/ci/taskcat-autobucket.yml
[taskcat] |Queing test => taskcat-test1
[INFO   ] :Creating bucket taskcat-tag-sample-taskcat-project-5d32eb7c in us-east-1
[INFO   ] :Staging Bucket => [taskcat-tag-sample-taskcat-project-5d32eb7c]
[INFO   ] :Multithread upload enabled, spawning 16 threads
[S3: -> ] s3://taskcat-tag-sample-taskcat-project-5d32eb7c/sample-taskcat-project/ci/debug-input.json
[S3: -> ] s3://taskcat-tag-sample-taskcat-project-5d32eb7c/sample-taskcat-project/ci/taskcat-autobucket.yml
[S3: -> ] s3://taskcat-tag-sample-taskcat-project-5d32eb7c/sample-taskcat-project/ci/taskcat.yml
[S3: -> ] s3://taskcat-tag-sample-taskcat-project-5d32eb7c/sample-taskcat-project/scripts/scripts_userdata.sh
[S3: -> ] s3://taskcat-tag-sample-taskcat-project-5d32eb7c/sample-taskcat-project/templates/debug-yaml.template
[S3: -> ] s3://taskcat-tag-sample-taskcat-project-5d32eb7c/sample-taskcat-project/templates/debug.template
[taskcat] |Contents of S3 Bucket
```
