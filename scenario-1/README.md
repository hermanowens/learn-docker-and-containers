# Deploying Your First Docker Container

Learn how to launch containers using Docker.

## What I learned: (This scenario used Redis as example)
- How to search for existing docker images:
    ```
    docker search <name>
    ```

    ```
    docker search redis
    ```

- How to list all running commands:
    ```
    docker ps
    ```
    ***Note: This will also provide a friendly name and container ID that can be used display more details about the container or display messages the container has written. __See next 2 bullets for information.__

- How to display details about container:
    ```
    docker inspect <friendly-name | container-id>
    ```

- How to display logs from container:
    ```
    docker logs <friendly-name | container-id>
    ```

- How to discover which port has been assigned to a randomly available port.
    ```
    docker port redisDynamic 6379
    ```
    or
    ```
    docker ps
    ```
    ***Note: This command is associated to __Task 3__ below.

- How to remove a container:
    ```
    docker rm <friendly-name | container-id>
    ```

- How to launch ubuntu container execute the running processes command:
    ```
    docker run ubuntu ps
    ```

- How to access bash shell inside of a container:
    ```
    docker run -it ubuntu bash
    ```

### Tasks:
1. Run docker redis container in the background.
    ```
    docker run -d redis:latest
    ```
    ***Note: I wrote `docker run -d redis`. Either works fine, but it's best to include a tag or version after the  ':'.
2. Run a docker redis container in the background that has a defined name and ports.
    ```
    docker run -d --name redisHostPort -p 6379:6379 redis:latest
    ```
    ***Note: I wrote the exact command as displayed above.
3. Run a docker redis container in the  background that has a name and a dynamic port.
    ```
    docker run -d --name redisDynamic -p 6379 redis:latest
    ```
4. Run a docker redis container in the background that has a name and is mapped to a volume on the host to persist data.
    ```
    docker run -d --name redisMapped -v "$PWD/data":/data redis
    ```
