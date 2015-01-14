# logstash-log4j2

Log4j2 plugin for logstash.

## Supported Log4J2 versions:
Version: 2.1+

## Get the plugin

### Logstash 1.5+

Use the install method

```$LS_HOME/bin/plugin install logstash-input-log4j2```

### Logstash 1.4

Download the latest release at: https://github.com/jurmous/logstash-log4j2/releases and unzip it.

If you download the source you also need rake to run ```rake vendor``` to download the correct log4j2 jars.

To run the plugin you need to start logstash with the plugin path `./bin/logstash --pluginpath PATH_TO_PLUGIN -f YOUR_CONF.conf`

## Setup log4j2
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

## Setup Logstash

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
