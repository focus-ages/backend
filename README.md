## Local Docker Development

To run the application locally using Docker, follow these steps:

1. Create a file named `local-docker-compose.yaml` in the root directory of your project.
2. Add the following content to the file:

    ```yaml
    version: '3'

    services:
        focus-api:
            build: .
            env_file:
                - .env
            ports:
                - '8080:8080'
    ```

    This defines a Docker Compose service named `focus-api` that builds the application using the Dockerfile in the current directory, sets environment variables from the `.env` file, and exposes port `8080`.

3. Run the following command to start the service:

    ```
    docker compose -f local-docker-compose.yaml -p local-focus-api up
    ```

    This will start the service and output the logs to the console. You can then access the application at `http://localhost:8080`.

## Production Deployment

To deploy the application to production, you can use render.com or any other provider that supports docker.

Follow these steps to deploy on render.com:

1. Create an account on render.com and log in.
2. Follow the instructions on the render.com documentation (https://render.com/docs) to create a new web service and select "Docker" as the environment.
3. In the "Dockerfile Path" field, enter the path to the Dockerfile.
4. Set the environment variables for the application by clicking on the "Environment" tab and adding the variables.
5. Click on the "Create Web Service" button to create your service.
6. Once the service is created, it can be accessed by clicking on its name on the dashboard.

## Request format

To generate phrases, send a POST request to `/frases` with the following JSON payload:

```json
{
    "goals": ["goal"]
}
```
