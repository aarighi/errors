# Spring Boot

This refers only to Spring Boot with annotations (no XML)

## SSL

One of the most common errors that pops out when calling an `https://` endpoint from a Spring Boot Application is

```
sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target
```

Which is often caused by a self-signed certificate **or** certificate not loaded in the Java keystore.

### 1. Check Java version
Java 8 doesn't support LetsEncrypt certs up to build `8u101` ([source](https://community.letsencrypt.org/t/certificate-error-sun-security-validator-validatorexception-pkix-path-building-failed-sun-security-provider-certpath-suncertpathbuilderexception-unable-to-find-valid-certification-path-to-requested-target/28283/2))
and maybe that's the cause. Check it with:

    java -version


### 2. Check your trust store
If the version is ok, chances are that the destination certificate is not loaded in the JVM keystore.

#### Find your keystore
First of all, check which keystore your app is currently using.

You application.properties (or .yml) may contain the following entry:

    server.ssl.key-store=/path/to/some/keystore
    
in which case, you know where to look.

Otherwise, the default JVM store is used, which can be found in either 
  * `$JDK_HOME/jre/lib/security/cacerts` (JDK folder) or 
  * `$JAVA_HOME/lib/security/cacerts` (JRE folder)
NOTE: `cacerts` is the file you are looking for, and not a folder.

If you have both of these files, better repeat the [_**Import**_](#import) step for them all.

#### Download the certificate
As the title says.

Open from your browser the domain you want to call. Download the certificate - you usally do it from a menu that can be reached from the lock icon in your address bar - and save it as `.der` or `.crt`.

#### Import
the certificate in the trust store.

Use the following command - ** use a custom value for `-alias`**:

    keytool -import -alias my-cert -keystore /path/to/keystore -file path/to/certificate.crt
    
### 3. Restart your application
After step 2, restart the application. Should work.
