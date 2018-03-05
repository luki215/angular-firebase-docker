[![Greenkeeper badge](https://badges.greenkeeper.io/bartholomej/angular-firebase-docker.svg)](https://greenkeeper.io/)

# Angular CLI + Firebase: Docker image

> Lightweight Docker image based on NodeJS 9 with:
- NodeJS 9.x
- Angular CLI 1.7.2+
- Firebase Tools 3.17.4+
- Yarn 1.5.1+


## Examples

### Bitbucket Pipelines CI

Deploy your Angular 2 project with Bitbucket Pipelines to Firebase Hosting

#### Firebase

- Create Firebase project

#### Firebase token

- Install firebase-tools locally `npm install -g firebase-tools`
- Get the `$FIREBASE_TOKEN` on firebasetool by running:

`firebase login:ci`

#### Environment variables

- Save it to Bitbucket's environment variables `(Project -> Settings > Environment variables)` with variable name `FIREBASE_TOKEN`

#### Pipelines configuration

- Create `bitbucket-pipelines.yml`


```yml
image: bartholomej/angular-firebase

pipelines:
  branches:
    master:
    - step:
        caches:
          - node
        script:
          - yarn
          - yarn build
          - firebase deploy --token "$FIREBASE_TOKEN"
```

#### Conclusion

And now every commit pushed to `master` branch will deploy your changes to Firebase

## Docker hub

Can be pulled from Docker Hub

```docker
docker pull bartholomej/angular-firebase
```