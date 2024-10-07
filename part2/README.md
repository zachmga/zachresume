# Deploy your Static Site on App Platform

[About App Platform](../docs/app_platform/README.md)

## **Step 1: Prepare Dockerfile and Commit Your Code**

Once your resume looks how you’d like it to, we are going to deploy it to DigitalOcean App Platform! 

In the root of your project, you create a `Dockerfile` and add the following to your `Dockerfile` :

```docker
FROM hugomods/hugo:exts

COPY . /src

# Build site.
RUN hugo --minify 

```

This Dockerfile copies the site source file to `/src`  and builds your site. 

<aside>

The *public/output directory* should be /src/public by default- this is used in subsequent steps

</aside>

Now, let’s create a `.gitignore` file in the root of the directory. Add the following to your `.gitignore` :

```
public
docs
img
README.md
```

Whenever your site is generated, it creates all of its files in the `/public` directory. We want to ignore these files because when we deploy our app to DigitalOcean, because when our Dockerfile runs, those files will be generated on the App Platform side. 

We’ll remove `docs`, `img`, and [`README.md`](http://README.md) as those aren’t needed to run your site, they’re just for assignment instructions.

Run `git status` to see all of the files that will be committed to your repository. 

Then run `git add .`  and `git commit -m "Your commit message here"` . Then push your changes to your repository. 

## **Step 2: Create a new App**

First, we need to create an app in App Platform:

1. Log in to your DigitalOcean account at `cloud.digitalocean.com` 
2. In the top middle right, select `Create` 
    
    ![Create App](../img/app_platform_create.png)
    
3. Select `App Platform` 
    
    In the App Configuration screen, you can choose the settings and sources for your app. Remember that we are now using Platform as a Service (PaaS), wherein the cloud platform handles all of the backend infrastructure for us. We aren’t provisioning VMs ourselves, we’re just telling the cloud where and how to run our code!
    
4. Our first option is to tell App Platform where our source code lives. Note that you have many options! If you want to deploy source code, you can choose GitHub or GitLab. If you wanted to deploy an application using a container image, you have the option of using Docker Hub, DigitalOcean Container Registry, or GitHub Container Registry. 
    
    We’ll choose GitHub. 
    

![Create Resource from Source Code](../img/app_platform_create_resource_from_source_code.png)

1. Next, we’ll give DigitalOcean App Platform access to our repository that contains our static site. 
    
    ![Select Repository](../img/app_platform_select_repository.png)
    
    I have already allowed DigitalOcean App Platform to have access to any repository created in the `MIS547-Fall24` GitHub organization. A new repository is created in MIS547 org every time a student accepts an assignment. Scroll down to the repositories that start with “Assignment-6” and then find yours, and select it. 
    

1. Then ensure that **Autodeploy code changes** is checked, and press **next** to continue. 

1. You’ll be taken to a page where App Platform has detected your app’s configuration. You’ll see the resources detected from the configuration for your app.

![Auto Detect Configuration](../img/app_platform_autodetect_config.png)

1. Click on “Edit” and then scroll down to see the Build Phase information. Under the “Build Command”, in the box, update the command as seen below. Click Save.

![Edit build command](../img/app_platform_build_command.png)

1. In the App Info section, next to the name of your app, select ‘Edit’. 

![Edit App Info](../img/app_platform_edit_app_info.png)

1. Change the project to Assignment 6 and click ‘Save’. 

![Change Project](../img/app_platform_assingment_6.png)

1. Under the ‘Review’ tab, review the configuration, then click Launch App. When your app is being deployed, you’ll have the opportunity to view the build logs by clicking on ‘Go to Build Logs’.

![Go to Build Logs](../img/app_platform_build_logs.png)

Once the build process completes, the interface will show you a healthy site and provide a link for you to visit the site. 

Now, whenever you make changes to your code and push the changes to your GitHub repository, the changes will be deployed on DigitalOcean! 

**In our next assignment, we’ll attach a custom domain to our App, as well as deploy some serverless code alongside it!**