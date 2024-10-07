# About App Platform

App Platform is a Platform-as-a-Service offering that allows developers to publish code directly to DigitalOcean servers without worrying about the underlying infrastructure. 

You can deploy apps from GitHub, GitLab, GitHub Actions, Docker Hub, DigitalOcean image repository, and more. You can choose from shared or dedicated resources based on your app or website needs, and enable smart autoscaling that suits your budget and growth plans. 

App Platform has a simple, flexible pricing with a free tier. You can host up to 3 static sites for free, and then are charged on a per-app basis after that (accounting for resource consumption.)

When you give App Platform access to your code, it will look for a Dockerfile in the root of the directory or specified in the app spec. Otherwise, App Platform checks your code to determine what language or framework it uses. If that language or framework is supported, App Platform will choose an appropriate resource type and use the proper `buildpack` to build the app and deploy a container. 

A buildpack is an open-source script that compiles apps as container images for a given programming language. Buildpacks provide a canonical way for containers to be created for all programming languages that need a stable and secure runtime and access to the right package managers to handle dependencies. 

Cloud Native Buildpacks are [open-source buildpacks built by Heroku](https://github.com/heroku/buildpacks). However, some buildpacks used in App Platform were built in-house at DigitalOcean. 

In our case, App Platform can detect that we’re using Hugo for static site generation by looking for the following files:

- config.toml
- config.yaml
- config.json

App Platform uses version `v1.8.0` of the Hugo Cloud Native Buildpack. If no version is specified, App Platform defaults to using version `v0.125.2` .

The buildback supports the following Hugo runtime versions:

- Ubuntu-22
    - 0.54.0-0.125.2
- Ubuntu-18
    - 0.54.0-0.125.2

You can specify a Hugo version by setting `HUGO_VERSION` environment variable to any valid release from Hugo’s upstream repository.