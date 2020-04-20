# Docker

## Cleanup

```bash
# Delete all containers (and volumes)
$ docker rm -vf $(docker ps -aq)

# Delete all images
$ docker rmi -f $(docker images -aq)
```
