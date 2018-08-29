# Blue-Green-Deployment
Blue-green deployments involve running two versions of an application at the same time and moving production traffic from the old version to the new version. There are several ways to implement a blue-green deployment in OpenShift Container Platform.

From CLI Create application: oc new-app openshift/deployment-example:v1 --name=example-green

From CLI Create application: oc new-app openshift/deployment-example:v2 --name=example-blue

From CLI Create route for example-green: oc expose svc/example-green --name=bluegreen-example

From CLI switch route from green to blu: oc patch route/bluegreen-example -p '{"spec":{"to":{"name":"example-blue"}}}'

In your browser, refresh the page until you see the v2 image.
