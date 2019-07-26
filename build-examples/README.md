# Build Creation

## Docker Build
#### Steps:
##### Create our resources:
```
oc create -f docker.yml
```
##### Wait until our build will be completed:
```
oc get build
```
##### Run our build:
```
oc start-build docker-build
```
##### Check that our build is ok: 
```
oc get build
```

## Pipeline Build
#### Novice Steps:

##### Make the Docker Build without two last steps.

##### Create our resources:
```
oc create -f pipeline-novice.yml
```
##### Wait until our build will be completed:
```
oc get build
```
##### Run our build:
```
oc start-build pipeline-novice-build
```
##### Check that our build is ok: 
```
oc get build
```

#### Intermediate and Advanced Steps:
##### Create our resources:
 ```
oc create -f pipeline-intermediate.yml / oc create -f pipeline-advanced.yml
```
##### Wait until our build will be completed:
```
oc get build
```
##### Run our build:
```
oc start-build pipeline-intermediate-build / oc start-build pipeline-advanced-build
```
##### Check that our build is ok: 
```
oc get build
```

## S2I Build
 
#### Steps:
##### Create an ImageStream for python 
```
oc create is python
```
##### Create our build:
```
oc new-build https://github.com/enybor/pyjwt_example --name=s2i-build --allow-missing-imagestream-tags=true --to=s2i-pyjwt-app
```
##### Wait until our build will be completed:
```
oc get build
```
##### Run our build:
```
oc start-build s2i-build
```
##### Check that our build is ok: 
```
oc get build
```


## Custom Build 
By default Custom Build Type is turned off for authenticated users and we have to update policy for them:
```
oc login -u system:admin
oc policy add-role-to-group system:build-strategy-custom system:authenticated
oc policy who-can create builds/custom
```
 
If we want to clean:
```
oc policy remove-role-from-group system:build-strategy-custom system:authenticated
```
 
#### Steps:
##### Create our resources: 
```
oc create -f custom.yml
```
##### Wait until our build will be completed:
```
oc get build
```
##### Run our build:
```
oc start-build custom-build
```
##### Check that our build is ok: 
```
oc get build
```