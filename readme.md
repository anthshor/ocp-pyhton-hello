## Project for OCP

Commands
```
oc new-project test
oc new-app https://github.com/anthshor/ocp-python-hello --strategy=docker
oc get pods
oc status
oc expose svc/ocp-python-hello
oc get routes
```

Log
```
oc new-project test

oc new-app https://github.com/anthshor/ocp-pyhton-hello --strategy=docker
    --> Found Docker image ca96bab (3 weeks old) from Docker Hub for "python:2.7-slim"

        * An image stream will be created as "python:2.7-slim" that will track the source image
        * A Docker build using source code from https://github.com/anthshor/ocp-pyhton-hello will be created
        * The resulting image will be pushed to image stream "ocp-pyhton-hello:latest"
        * Every time "python:2.7-slim" changes a new build will be triggered
        * This image will be deployed in deployment config "ocp-pyhton-hello"
        * Port 8090 will be load balanced by service "ocp-pyhton-hello"
        * Other containers can access this service through the hostname "ocp-pyhton-hello"
        * WARNING: Image "python:2.7-slim" runs as the 'root' user which may not be permitted by your cluster administrator

    --> Creating resources ...
        imagestream "python" created
        imagestream "ocp-pyhton-hello" created
        buildconfig "ocp-pyhton-hello" created
        deploymentconfig "ocp-pyhton-hello" created
        service "ocp-pyhton-hello" created
    --> Success
        Build scheduled, use 'oc logs -f bc/ocp-pyhton-hello' to track its progress.
        Application is not exposed. You can expose services to the outside world by executing one or more of the commands below:
        'oc expose svc/ocp-pyhton-hello' 
        Run 'oc status' to view your app.

oc get pods
    NAME                       READY     STATUS    RESTARTS   AGE
    ocp-pyhton-hello-1-build   1/1       Running   0          15s

oc status
    In project test on server https://192.168.99.100:8443

    svc/ocp-pyhton-hello - 172.30.119.59:8090
    dc/ocp-pyhton-hello deploys istag/ocp-pyhton-hello:latest <-
        bc/ocp-pyhton-hello docker builds https://github.com/anthshor/ocp-pyhton-hello on istag/python:2.7-slim 
        deployment #1 deployed 9 seconds ago - 1 pod


    2 infos identified, use 'oc status -v' to see details.

oc expose svc/ocp-pyhton-hello
    route "ocp-pyhton-hello" exposed

oc get routes
    NAME               HOST/PORT                                     PATH      SERVICES           PORT       TERMINATION   WILDCARD
    ocp-pyhton-hello   ocp-pyhton-hello-test.192.168.99.100.nip.io             ocp-pyhton-hello   8090-tcp                 None
```

### Test
Browse to <route URL>
  
e.g
```
http://ocp-pyhton-hello-test.192.168.99.100.nip.io
```


Based from
https://docs.docker.com/get-started/part2/


