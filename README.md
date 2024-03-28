# Docker based examples of UD-Viz

This container packages the TunNetView
[TunNetView application](https://github.com/VCityTeam/TunNetView).

Build the docker image with

```bash
docker build -t vcity/tunnetview https://github.com/VCityTeam/TunNetView-docker.git -f Context/Dockerfile
```

Additionnaly you might wish to specify a [TunNetView](https://github.com/VCityTeam/TunNetView)
commit number e.g.

```bash
docker build --build-arg checkoutName=9e79839f158f4  -t vcity/tunnetview https://github.com/VCityTeam/TunNetView-docker.git -f Context/Dockerfile
```

Then run the container e.g. with

```bash
docker run -p 0.0.0.0:8000:8080/tcp [--detach] --rm -t vcity/tunnetview
```

and open a web browser on URL `http://localhost:8000/`

Notes:

- you can specify the branch or a commit in the build arg `checkoutName` (*default = master*) 
- in the above `docker run` command the optional `--detach` argument requires the
  container to run in background (detached mode),
- the published port (the `8000` in the above `-p` flag argument of the the
  `docker run` command) can be changed but has to match with the port given
  (within the URL) when browsing

TunNetView sources are available through the 
[TunNetView github repository](https://github.com/VCityTeam/TunNetView).
