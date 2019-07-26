# Deployment

### Prerequisites
- login as you developer user
- create your own project

### Example:
#### Use `developer/developer` credentials:
```
oc login
oc new-project testproject
oc project testproject
```

## Simple Deployment
#### Creation Steps:
##### Create our resources:
```
oc create -f simple-app.yml
```
##### Create a route for our service:
```
oc expose service pyjwt-app-svc
```
##### Use route to get an access in a browser:
```
oc start-build docker-build
```
#### Testing Steps:
##### Go to `/auth` to get token.
##### Go to  `/unprotected` and check the access.
##### Go to  `/protected?token=<put_token_here>` and check the access.

