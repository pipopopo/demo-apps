[https://quarkus.io/guides/cli-tooling#installing-the-cli](https://quarkus.io/guides/cli-tooling#installing-the-cli)
The Quarkus CLI is available as a jar installable using JBang.
JBang will use your existing Java or install one for you if needed.

On Linux, macOS, and Windows (using WSL or bash compatible shell like Cygwin or MinGW)
```
curl -Ls https://sh.jbang.dev | bash -s - trust add https://repo1.maven.org/maven2/io/quarkus/quarkus-cli/
curl -Ls https://sh.jbang.dev | bash -s - app install --fresh --force quarkus@quarkusio
```

[https://quarkus.io/guides/deploying-to-openshift](https://quarkus.io/guides/deploying-to-openshift)
Bootstrapping the project

Create a new project with the Openshift extension
```
quarkus create app kenny:openshift-quarkus --extension='resteasy-reactive,openshift'
```

Go into the directory
```
cd openshift-quarkus
```

Point quarkus to Openshift URL (can be skipped if it's already loaded)
```
quarkus build -Dquarkus.kubernetes-client.api-server-url=Openshift-API-ServerURL
```

Build and deploy on Openshift:
```
quarkus build -Dquarkus.kubernetes.deploy=true
```

Expose route
```
oc expose svc/openshift-quarkus
```


