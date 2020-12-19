# Config File

Webtau let you specify services url, browser settings, DB url connections, etc in a config file.
Depending on [runner](getting-started/installation) you use webtau will read data from a different place.

## Groovy Standalone Runner

When you use the Groovy runner, it will look for `webtau.cfg.groovy` file (default). 

:include-file: examples/todo/webtau.cfg.groovy {title: "webtau.cfg.groovy"}

Note: webtau treats groovy config file as code

## JUnit Like Runners

When you use JUnit like runners, e.g. [JUnit5](getting-started/installation#junit5), webtau expects file named
`webtau.properties` to be present in test classpath, e.g. test resources:

:include-file: src/test/resources/webtau.properties {title: "src/test/resources/webtau.properties"}

# Overrides

Webtau has a list of options you can specify using config file: [url, browserId, etc.](configuration/options).
You can override any value using [environment variables](configuration/options#environment-variable-options):

```
export WEBTAU_URL=http://another-server
export WEBTAU_CHROME_DRIVER_PATH=/path/to/chrome/driver
``` 

In addition to environment variables, you can use a runner specific way to override:
 
## Groovy Standalone Runner

In case of Groovy standalone runner, pass `--<option>=<value>`:

:include-cli-command: webtau --waitTimeout=25000 --url=http://another-server

## JUnit Like Runners

Pass system property via java `-D` option:
```
-Durl=http://another-server
```