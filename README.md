# JMeter Armada

This solution looks to give software testers and other within the decvelopment cycle a harness to run JMeter scripts (.jmx files) distributed with multiple users without needing to create the infrastructure to manage it.

---
## In progress
This project is currently in progress and as such may not work corrrectly at this stage - I will be updating this readme as I update the code and also will remove this specific message when it's in a stable working state

---


## Introduction
A few years ago I was working as a Performance Tester for a company. As part of the project I was on I needed to test a website with 20,000 virtual users overnight. A soak test of sorts. At this point in my career I had been analysing performance metrics but never performed a large scale load test before.

I've always believed that there was a significant different Performance Testing and Load Testing:

- Load Testing was seeing how a system reacted under certain amount of load over periods of time
- Performance Testing was analysing the performance of an application or service, regardless of the load it is under

I had always been a Performance Tester, my application of choice being [Apache Jmeter](https://www.google.com) however now I needed to create many more users that I was accoustom to.

After some research I realised that I could generate these users through onlince cloud services like AWS. However this was time consuming and required a significant amount of AWS knowledge. Something that not all Testers would be able to obtain.

With the help of my wife; the Armada project became a reality. I could package up everything a budding software tester might need to take a "single-user load test in JMeter" to "near-infinite user load test" without spending months learning AWS skills or scripting.

The term 'Armada' originally came from the concept of this project mainly being contained within Docker containers, each docer container would generate a certain amount of load the the system - hence the analogy of seacraft. Now the name has stuck.

## Responsible Use
I built this solution to allow people to create lots of virtual users to use in their JMeter Testing. I'm aware that this may give raise to potential misuse. The ultimate responsiblity lies with yourself to obtain permission to load test any target that you are working on. Not doing so can get you into trouble and can eveen be seen as a DDoS attack.

This software was created to help Software Testers take the stress out of creating infrastructure. Nothing more. I do not accept responsibility for anything performed using this solution.

## Tutorial
Firstly, you'll need a couple of things set up...

- [Jmeter 5.0 or higher installed](google.com)
- [An AWS Account](www.google.com)
- [The AWS CLI toolkit installed](google.com)
- [A KeyPair for EC2 instances](google.com)

## Current Workflow
- You have a script created in JMeter (installed with NO ADDITIONAL PLUGINS)
- You run the Launch-Armada script - this creates the following within the eu-west-1 (Virginia) region:
    - S3 Bucket
    - Launch Template
    - VPC
    - Internet Gateway
    - VPC Gateway Attachment
    - Subnet within the VPC
    - Route Table
    - Internet Routing
    - Subnet Route Table Association
    - Security Group
    - EC2 Instance
    - Spot Fleet
- You then move your test script to the S3 Bucket
- You then invoke the "Jmeter, Run my test" command 
- The test then runs, moving the resulting files (the .jtl files) into the S3 bucket
- You then navigate to www.link.com and view the folders within that bucket
- You navigate to the most recent test results for analysis
- You then issue the 'Remove Armada' Script, this will gracefully remove all the associated resources from AWS

## Starting point
I'll assume that you're starting from this point - you have a JMeter test file (a .jtl file) that you're about to run locally and want to take this test to the next level.

## Running this test on the CLI
//todo

## Running the test on the Armada

## Next Steps
If you have any suggestions on how to improve this solution then please reach out either on [LinkedIn](google.com) or [Twitter](google.com); I'm always happy to talk about stuff like this.

If you want to fork this and make your own version then that's absolutely find under the GNU license, all I ask is that you attribute this repo when you're publishing it.

Thank you

## Stretch Goals/Future Work
- A GUI to allow people to upload their JTL files, run them and have a graphical interface to see the load test
- Presenting the results as an HTML page dynamically
