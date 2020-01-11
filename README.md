## Compiling my quick learnings 

Following are the steps that I followed for running JMeter tests using the maven jmeter plugin in distributed mode.

1. Generated a keystore by following the instructions detailed [here](https://github.com/jmeter-maven-plugin/jmeter-maven-plugin/wiki/Remote-Server-Configuration#distributed-testing-pre-requisite) and copied the newly generated keystore into `src/test/conf/`

2. Now started the jmeter-server using the command 

```
export RMI_HOST_DEF=-Djava.rmi.server.hostname=192.168.0.101 && ./jmeter-server
```

3. Now to run the jmeter tests in local mode, run the command 

```
mvn clean verify
```

and to run the tests in distributed mode, run the command

```
mvn clean verify -P ci -Dservers=<JMeterServerIpGoesHere>
```

## References

1. https://www.vinsguru.com/jmeter-continuous-performance-testing-jmeter-maven/
2. https://www.blazemeter.com/blog/how-use-jmeter-maven-plugin/
3. https://github.com/justb4/docker-jmeter
4. https://medium.com/@DragosCampean/how-to-build-a-distributed-load-testing-infrastructure-with-aws-docker-and-jmeter-accf3c2aa3a3
5. Complete plugin configuration sample available [here](https://github.com/jmeter-maven-plugin/jmeter-maven-plugin/blob/master/src/it/remote-test/pom.xml#L36-L109)
6. https://github.com/jmeter-maven-plugin/jmeter-maven-plugin/issues/354
