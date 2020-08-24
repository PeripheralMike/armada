# armada

This project will allow people to distribute their JMeter .jmx files to multiple individual machines using AWS.

This will also give people the option to run them from containers using Docker if they wish.

This will give people near unlimited numbers of virtual users to test their system without needing to worry about the infrastructure behind the distribution.

## Running the test normally on the CLI

```
 sh jmeter.sh -n -t sampletest.jmx
```
