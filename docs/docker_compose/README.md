# About Docker Compose

We’ll use Docker Compose in more depth in coming assignments. Using Docker Compose in this assignment is designed to give you a very high-level introduction.

### What is Docker Compose?

Docker Compose is a tool for defining and running multi-container applications. It helps us streamline our development and deployment experience. 

Docker Compose functionality is handled by writing a YAML-based configuration file. Then, with a single command, you create and start all the services from your configuration file. 

Compose works in production, staging, development, testing, as well as with CI workflows. 

It also has commands for managing the whole lifecycle of your application. 

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