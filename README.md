# external_tomcat_configuration

The need for external_tomcat_configuration came about at a customer who needed to change the contents of `server.xml` to allow an unlimited numbers of parameters to be passed into the service.
The alternative - to re-write the code - was estimated at 500hrs, so the "hack" made sense.

The solution involves adding an environment variable to the `manifest.yml` file for the `cf push` 

```
JBP_CONFIG_TOMCAT: '{ tomcat: { external_configuration_enabled: true }, external_configuration: { repository_root: "http://github.com/rm511130/external_tomcat_configuration/blob/master/" } }'
```

All good, except for the fact that it didn't quite work... so we opened a support ticket.

Links we based ourselves on:

- https://github.com/cloudfoundry/java-buildpack/blob/master/docs/container-tomcat.md#additional-resources
- https://github.com/cloudfoundry/java-buildpack/blob/master/docs/extending-repositories.md
- https://github.com/swisscom/tomcat-external-configuration
- https://github.com/cloudfoundry/java-buildpack/issues/316
- http://tomcat.apache.org/tomcat-8.0-doc/config/resources.html#Common_Attributes
- https://stackoverflow.com/questions/315093/configure-symlinks-for-single-directory-in-tomcat
