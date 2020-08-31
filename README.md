# armada

This project will allow people to distribute their JMeter .jmx files to multiple individual machines using AWS.

This will also give people the option to run them from containers using Docker if they wish.

This will give people near unlimited numbers of virtual users to test their system without needing to worry about the infrastructure behind the distribution.

## Running the test normally on the CLI

```
 sh jmeter.sh -n -t sampletest.jmx
```


## Requirements 
AWS CLI
A Jmeter Test Script
An AWS account

## Creating the keypair
This will allow you to create a keypair for this exercise

```
aws ec2 create-key-pair --key-name armada-sandbox --query 'KeyMaterial' --output text > armada-sandbox.pem && chmod 400 armada-sandbox.pem
```

