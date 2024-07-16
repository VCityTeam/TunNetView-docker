# Docker based examples of TunNetView

This repository illustrates how to use
[TunNetView application](https://github.com/VCityTeam/TunNetView) with docker.

## Build the docker image with

```bash
docker build -t vcity/tunnetview https://github.com/VCityTeam/TunNetView-docker.git -f Context/Dockerfile
```

Additionnaly you might wish to specify a [TunNetView](https://github.com/VCityTeam/TunNetView)
commit number e.g.

```bash
docker build --build-arg checkoutName=9e79839f158f4  -t vcity/tunnetview https://github.com/VCityTeam/TunNetView-docker.git -f Context/Dockerfile
```

## Run the resulting container

### A simple run of the container

The commande goes
```bash
docker run -p 0.0.0.0:8000:8080/tcp [--detach] --rm -t vcity/tunnetview
```

and open a web browser on URL `http://localhost:8000/`

Notes concerning the above argument:

- you can specify the branch or a commit in the build arg `checkoutName` (*default = master*) 
- in the above `docker run` command the optional `--detach` argument requires the
  container to run in background (detached mode),
- the published port (the `8000` in the above `-p` flag argument of the the
  `docker run` command) can be changed but has to match with the port given
  (within the URL) when browsing

### Using environment variables to parametrize the container run

[TunNetView recognizes environment variables](https://github.com/VCityTeam/TunNetView/blob/master/Readme.md#runtime-environment-variables) that can be used by docker.
For example you might try

```bash
docker run [--detach] --rm -e PORT='8080' -e SYNTHETIC_CAVE_URL=https://dataset-dl.liris.cnrs.fr/synthetic-cave-and-tunnel-systems/Cave/cave_sub_1_grid_size_x_1_grid_size_y_1_point_cloud-3dtiles/tileset-translated-to-lyon-cathedral.json -t vcity/tunnetview
```
