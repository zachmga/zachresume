# About Docker Compose

We’ll use Docker Compose in more depth in coming assignments. Using Docker Compose in this assignment is designed to give you a very high-level introduction.

### What is Docker Compose

Docker Compose is a powerful tool that simplifies the process of managing multi-container Docker applications. While Docker itself handles individual containers, Docker Compose allows developers to define and orchestrate multiple containers as a single application using a YAML configuration file. This file describes all the services, networks, and volumes required for your application, making it easy to reproduce the entire environment consistently across different systems.

With Docker Compose, developers can specify their application infrastructure requirements, including container images, environment variables, port mappings, volume mounts, and dependencies between services. For example, a typical web application might include containers for the web server, database, cache, and message queue. Instead of managing each container separately with complex Docker commands, developers can define all these components in the Compose file and launch the entire stack with a single command: `docker compose up`.

One of the key advantages of Docker Compose is its ability to create isolated environments for development, testing, and staging. When you run a Compose file, it automatically creates a dedicated network for your application's containers, allowing them to communicate with each other while remaining isolated from other applications on the host system. This isolation, combined with the ability to share Compose files among team members, ensures consistency across different development environments and eliminates the "it works on my machine" problem.

Beyond basic container orchestration, Docker Compose supports advanced features such as scaling services, managing container lifecycles, and handling service dependencies. It can automatically restart failed containers, wait for dependent services to be ready before starting a container, and even scale specific services to multiple instances. This makes Docker Compose an invaluable tool for both development workflows and simple production deployments, though for more complex production environments, container orchestration platforms like Kubernetes are often preferred.

### What Can We Do with Docker Compose?

With Docker Compose, you use the Compose file to configure your application’s services, and then run them using the Compose CLI. 

We can define multi-container applications by using the compose specifications:

- Computing components of an application are defined as **services**.
- Services communicate with each other through **networks.**
- Services store and share persistent data into **volumes.**
- Some services require configuration data that depends on the runtime or platform. We can set these using **configs**. Configs are comparable to volumes in that they are files mounted into the container.
- **Secret** is an instance of configuration data for anything that should not be exposed without security considerations. Secrets are made available to services as files mounted into their containers, but the platform-specific resources to provide sensitive data are specific enough to deserve a distinct concept.
- We define a **project** as an individual deployment of an application specification on a platform. A project’s name is set with the top-level **name** attribute. The name helps us group resources together and isolate them from other applications or installations of the same compose-specified application with distinct parameters.

The compose file can be called any of the following:

- `compose.yaml`
- `compose.yml`
- `docker-compose.yaml`
- `docker-compose.yml`

If multiple files exist, Compose prefers `compose.yaml` 

### Key Commands

To start all services defined in your `compose.yaml` file:

```
docker compose up
```

To stop and remove the running services:

```
docker compose down
```

If you want to monitor the output of your running containers and debug issues, you can view logs with:

```
docker compose logs
```

To list all the services along with their current status:

```
docker compose ps
```