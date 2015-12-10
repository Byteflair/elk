# elk
Docker compose file to orchestrate an ELK stack

If you are using logback for logging you can use the following configuration

```
<configuration scan="true" scanPeriod="30 seconds">
    <contextName>api</contextName>
    <variable name="host" value="localhost"/>
    <variable name="port" value="5000"/>
    <appender name="STDOUT" class="ch.qos.logback.core.ConsoleAppender">
        <encoder>
            <pattern>%d{HH:mm:ss.SSS} [%thread] %-5level %logger{36} - %msg%n</pattern>
        </encoder>
    </appender>
    <appender name="STASH" class="net.logstash.logback.appender.LogstashSocketAppender">
        <remoteHost>${host}</remoteHost>
        <port>${port}</port>
    </appender>
    <root level="INFO">
        <appender-ref ref="STDOUT"/>
        <appender-ref ref="STASH"/>
    </root>
</configuration>
```
