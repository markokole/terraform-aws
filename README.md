# terraform-aws
 Docker image for terraform for AWS

Rename the aws/credentials.template to /aws/credentials and add key and secret. Change the region accordingly.

The container has volume */local-git* which can be used to map local folder to that folder in the container. The idea is to execute the code from the container while writing code in the IDE of your choice. (Perhaps this only applies Windows users?)


```bash
docker build --file Dockerfile-terraform --tag=markokole/terraformer .
```

```bash
docker push markokole/terraformer
```

```bash
docker run -itd --name terraformer --env-file "aws/credentials" markokole/terraformer
```

```bash
docker exec -it terraformer /bin/sh
```
