logstash-log4j2
===============

Log4j2 plugin for logstash.

Supported Log4J2 versions:
-----
Version: 2.0 (And probably newer 2.x releases)

Get the plugin
----
Download the latest release at: https://github.com/jurmous/logstash-log4j2/releases and unzip it.

Setup log4j2
------------

Set log4j2.xml in your project
```xml
<?xml version="1.0" encoding="UTF-8"?>
<Configuration>
    <Appenders>
        <Socket name="A1" host="localHost" port="7000">
            <SerializedLayout />
        </Socket>
    </Appenders>
    <Loggers>
        <Root level="debug">
            <AppenderRef ref="A1"/>
        </Root>
    </Loggers>
</Configuration>
```

Setup logstash
-----

```
input {
  log4j2 {
    port => 7000
    mode => "server"
  }
}

output {
  stdout { codec => rubydebug }
}
```

Run logstash with the plugin
-------------

Run from your logstash install directory `./bin/logstash --pluginpath PATH_TO_PLUGIN -f YOUR_CONF.conf`
