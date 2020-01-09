## Compiling my quick learnings 

Following are the steps that I followed for running JMeter tests using the maven jmeter plugin in distributed mode.

1. Generated a keystore by following the instructions detailed [here](https://github.com/jmeter-maven-plugin/jmeter-maven-plugin/wiki/Remote-Server-Configuration#distributed-testing-pre-requisite) and copied the newly generated keystore into `src/test/conf/`
2. In the JMeter installation in the remote machine, opened up `user.properties` file in `/jmeter/apache-jmeter-5.2.1/bin` and updated the below properties

```
########################################################################
################## DISTRIBUTED TESTING CONFIGURATION  ##################
########################################################################
# Type of keystore : JKS
#
server.rmi.ssl.keystore.type=JKS
#
# Keystore file that contains private key
#
server.rmi.ssl.keystore.file=/jmeter/apache-jmeter-5.2.1/rmi_keystore.jks
#
# Password of Keystore
#
server.rmi.ssl.keystore.password=changeit
#
# Key alias
#
server.rmi.ssl.keystore.alias=rmi
```

3. Now started the jmeter-server using the command 

```
export RMI_HOST_DEF=-Djava.rmi.server.hostname=192.168.0.101 && ./jmeter-server
```

4. Now to run the jmeter tests in local mode, run the command 

```
mvn clean verify
```

and to run the tests in distributed mode, run the command

```
mvn clean verify -P ci -Dip=<IP_Address_Goes_Here>
```

## References

1. https://www.vinsguru.com/jmeter-continuous-performance-testing-jmeter-maven/
2. https://www.blazemeter.com/blog/how-use-jmeter-maven-plugin/


