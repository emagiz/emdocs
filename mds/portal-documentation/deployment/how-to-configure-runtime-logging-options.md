
How to configure custom runtime logging options
https://my.emagiz.com/link/documentation/4
In every runtime mode eMagiz is configured with some default logging options, but these can be overridden when required (for example, for debugging purposes). The default settings per runtime mode and ways to override them are described in the next paragraphs.
 
Default runtime
The default runtime (i.e. running from a command prompt using run-in-console.cmd on Windows or run-in-console.sh on Linux) has the most flexible logging options. By default all messages of level INFO and higher are displayed in the console window in shortened form, and written to the logs/emagiz.log log file with full details. This log file is archived and zipped every month or when it reaches a size of 100 MiB, whichever happens first.

You can override these default settings by specifying your own log settings. To do this, create a settings XML file and specify the name of this file as the CUSTOM_LOGBACK_CONFIG parameter in the run-in-console.cmd or run-in-console.sh file. A good starting point for creating your own settings XML file would be the default settings, which are as follows:

     <?xml version="1.0" encoding="UTF-8"?>
     <configuration>
        <appender name="FILE" class="ch.qos.logback.core.rolling.RollingFileAppender">
          <file>logs/emagiz.log</file>
          <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
              <fileNamePattern>logs/emagiz_%d{yyyy-MM}_%i.log.zip</fileNamePattern>
              <timeBasedFileNamingAndTriggeringPolicy class="ch.qos.logback.core.rolling.SizeAndTimeBasedFNATP">
                <maxFileSize>100MB</maxFileSize>
              </timeBasedFileNamingAndTriggeringPolicy>
              <maxHistory>12</maxHistory>
            </rollingPolicy>
            <encoder>
              <pattern>%date - %-5level [%logger] : %message%n%xException</pattern>
              <immediateFlush>true</immediateFlush>
            </encoder>
         </appender>
         <appender name="CONSOLE" class="ch.qos.logback.core.ConsoleAppender">
           <encoder>
             <pattern>%date{HH:mm:ss.SSS} - %-5level [%logger{0}] : %message%n%exception{short}</pattern>
             <immediateFlush>true</immediateFlush>
           </encoder>
         </appender>
         <root level="INFO">
           <appender-ref ref="FILE"/>
           <appender-ref ref="CONSOLE"/>
         </root>
       </configuration>
       
  For more information about logging options and the XML syntax, see the Logback manual.

 
Service runtime
When running eMagiz as a Windows service, the logging options are configured in the .ini file of the service. By default, all logging events of level INFO or higher are written to the file logs/emagiz.log with very detailed information. This log file is archived and zipped every month or when it reaches a size of 100 MiB, whichever happens first.

You can override these default settings by specifying different values for any of the following settings in the .ini file of the Windows service:

| Setting | Default Value | Description |
| :---: | :---: | :---: |
| emagiz.log | logs/emagiz.log | Name for the log file, relative to the working directory. |
| emagiz.log.level | INFO | Events of this level and higher are written to the log. Possible options are: ALL, TRACE, DEBUG, INFO, WARN, ERROR or NONE. Note that setting this lower than INFO is not recommended for production environments, as it might result in a significant performance overhead. |
| emagiz.log.pattern | %date - %-5level [%logger] : %message%n%xException | Pattern describing the layout of log lines. See the Logback manual for the syntax and all possible options. |
| emagiz.log.immediate-flush | true | If true, logging events are written to the log file immediately. This guarantees that events are never lost during a system crash. Setting this to false will probably increase performance quite a bit as events are buffered before writing them to the log file, but events might get lost during a system crash. |
| emagiz.log.roll.policy | logs/emagiz_%d{yyyy-MM}_%i.log.zip_ | Determines the log roll policy, i.e. when and how old log files are archived. See the Logback manual for the syntax and all possible options. |
| emagiz.log.roll.max-size | 100MB | The maximum size the log file is allowed to grow before it is archived. |
| emagiz.log.roll.history | 12 | The maximum number of archived log files to keep on disk. |  


## Mendix runtime

When running eMagiz in Mendix, all the logging of eMagiz is redirected to the Mendix logging mechanism. This means that to change any log settings, simply change the Mendix log settings.

There is one special setting for eMagiz logging in a Mendix Business Server, which is specified by the LogLevel constant of the EMagiz_Runtime module. This log level determines what eMagiz logging events are redirected to the Mendix logging mechanism. During development you'll probably want to set this to ALL: this way you can fully control all the log levels using the "Set log levels..." option in the Mendix Business Modeler. On a production server however, you'll probably want to set this to INFO: this completely suppresses all TRACE and DEBUG messages generated by eMagiz, resulting in a significant logging performance increase.
