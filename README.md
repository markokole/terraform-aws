# Local container for work with Amazon Web Services

The container has volume */local-git* which can be used to map local folder to that folder in the container. The idea is to execute the code from the container while writing code in the IDE of your choice. (Perhaps this only applies Windows users?)

```bash
docker build --file Dockerfile-terraform --tag=markokole/terraformer:1.0.3 --build-arg TERRAFORM_VERSION=1.0.3 .
```

Make sure to use the Terraform version as a tag as well!

## Push the image to the dockerhub

 **Make sure nå sensitive information is in the image!**

```bash
docker push markokole/terraformer:1.0.3
```

## Test the image locally

Run the container with the newly created image.

The following is not needed unless you plan to communicate with AWS:

Rename the aws/credentials.template to /aws/credentials and add key and secret. Change the region accordingly.

If only testing the container, drop the argument *--env-file*.

```bash
docker run -itd --name terraformer --env-file "aws/credentials" markokole/terraformer
```

Step into the container.

```bash
docker exec -it terraformer /bin/sh
```

The image was pushed to the docker hub and can also be retrieved using the following command:

```bash
docker pull markokole/terraformer:latest
```
