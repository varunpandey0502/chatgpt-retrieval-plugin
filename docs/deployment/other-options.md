# Other Deployment Options

Some possible other options for deploying the app are:

- **Azure Container Apps**: This is a cloud platform that allows you to deploy and manage web apps using Docker containers. You can use the Azure CLI or the Azure Portal to create and configure your app service, and then push your Docker image to a container registry and deploy it to your app service. You can also set environment variables and scale your app using the Azure Portal. Learn more [here](https://learn.microsoft.com/en-us/azure/container-apps/get-started-existing-container-image-portal?pivots=container-apps-private-registry).
- **Google Cloud Run**: This is a serverless platform that allows you to run stateless web apps using Docker containers. You can use the Google Cloud Console or the gcloud command-line tool to create and deploy your Cloud Run service, and then push your Docker image to the Google Container Registry and deploy it to your service. You can also set environment variables and scale your app using the Google Cloud Console. Learn more [here](https://cloud.google.com/run/docs/quickstarts/build-and-deploy).
- **AWS Elastic Container Service**: This is a cloud platform that allows you to run and manage web apps using Docker containers. You can use the AWS CLI or the AWS Management Console to create and configure your ECS cluster, and then push your Docker image to the Amazon Elastic Container Registry and deploy it to your cluster. You can also set environment variables and scale your app using the AWS Management Console. Learn more [here](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/docker-basics.html).

After you create your app, make sure to change the plugin url in your plugin manifest file [here](/.well-known/ai-plugin.json), and in your OpenAPI schema [here](/.well-known/openapi.yaml), and redeploy.

## Removing Unused Dependencies

Before deploying your app, you might want to remove unused dependencies from your [pyproject.toml](/pyproject.toml) file to reduce the size of your app and improve its performance. Depending on the vector database provider you choose, you can remove the packages that are not needed for your specific provider.

Find the packages you can remove for each vector database provider [here](removing_unused_dependencies.md).

After removing the unnecessary packages from the `pyproject.toml` file, you don't need to run `poetry lock` and `poetry install` manually. The provided Dockerfile takes care of installing the required dependencies using the `requirements.txt` file generated by the `poetry export` command.