## Open WebUI

https://docs.openwebui.com/

```bash
docker run -d -p 3000:8080 --add-host=host.docker.internal:host-gateway -v open-webui:/app/backend/data --name open-webui --restart no -e WEBUI_AUTH=false ghcr.io/open-webui/open-webui:main
```

Use `--restart always` instead of `--restart no` to always automatically start.

If you already set `--restart no` and want to change it, use `docker update --restart always open-webui`.

Check the status: `docker inspect -f "{{.HostConfig.RestartPolicy.Name}}" open-webui`

For NVIDIA GPU support, include the following argument:

```bash
--gpus all
```

## Update to Latest Version

Follow the `Manual Update` steps here: https://docs.openwebui.com/getting-started/updating/

Use the command above with the extra flags instead of the one provided in the documentation.

Probably want to run this to clean up the old image:

```
docker image prune
```
