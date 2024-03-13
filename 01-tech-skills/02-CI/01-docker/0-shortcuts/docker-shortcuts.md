# Docker shortcuts

To delete all containers including its volumes:

```bash
docker rm -vf $(docker ps -aq)
```

To delete all the images:

Remember, you should remove all the containers before removing all the images from which those containers were created.

```bash
docker rmi -f $(docker images -aq)
```
