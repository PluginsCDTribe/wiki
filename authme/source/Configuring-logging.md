The configuration file config.yml contains two settings that influence the logging that AuthMe will perform.

#### Security.console.logConsole (true / false)
If set to `true`, everything that AuthMe logs to the console will also be saved in authme.log. If a technical error occurs (called _Exception_ in Java), the full stacktrace is logged. This provides more technical details about the error, which are very interesting for us developers to know about.

#### settings.logLevel (INFO / FINE / DEBUG)
We recommend `FINE`. This logs, additionally to the INFO ones, some finer details which are still relevant and interesting to keep in a log. Use `DEBUG` if you're interested in seeing a lot of information from AuthMe. This is typically only used when you're trying to find the cause of an issue with AuthMe.
