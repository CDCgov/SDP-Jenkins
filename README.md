# SDP-Jenkins
This repository is meant to be used with Jenkins S2I on OpenShift to
install and enable the additional Jenkins plugins for the SDP project on
the official Jenkins image provided in OpenShift.

Create a Jenkins S2I build with this GitHub repository:
```
oc new-build jenkins:2~https://github.com/CDCgov/SDP-Jenkins.git --name=jenkins-sdp
```

Then you can deploy the Jenkins templates with the customized image. Replace
SDPJENKINS_IMAGE_NAMESPACE with the project where the above S2I build is created:
```
oc new-app jenkins-ephemeral \
    -p NAMESPACE=SDPJENKINS_IMAGE_NAMESPACE \
    -p JENKINS_IMAGE_STREAM_TAG=jenkins-sdp:latest
```
