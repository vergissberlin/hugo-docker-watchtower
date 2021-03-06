# Hugo Docker Watchdog - Continious dilivery

## Normal hugo stuff

1. Follow the [quickstart](https://gohugo.io/getting-started/quick-start/).
2. Install on of the themes. For this example, I've choosen the [UI-Kit](https://themes.gohugo.io//theme/hugo-now-ui/) [[repo](https://github.com/cboettig/hugo-now-ui)].
3. Add some demo pages from the examplePage of the theme
4. Push it to your reposistories (for instance on GitHub)

## What's the difference

1. The static page runs inside of a Container. It comes with a little webserver (NGINX)
2. The Docker registry on hub.docker.com is listening on changes in the master branch and build a new images with the current files automatically.
3. Watchertower checks for Docker images updates every 42 seconds. If there is a newer images available.
    1. It pulls the new image on the Docker host and
    2. it restarts the related running instances.

### Hints

1. In this example [Watchtower](https://containrrr.github.io/watchtower/) is running on same server aslike the static webpage, but it can run on remote servers also. For more information, take a look on the [documentation](https://containrrr.github.io/watchtower/usage-overview/).
2. On my webserver I use the jwilder HTTP proxy, to be able to have more than one application on the server which is exposing port 80 or 443. In addition I use Let's encrypt certificates. But this is ontoher topic. If you dont want this, just delete the lines in the `docker-compose.yml` file.