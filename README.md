# Hugo Docker Watchdog - Continious dilivery

## Normal hugo stuff

1. Follow the [https://gohugo.io/getting-started/quick-start/](quickstart).
2. Install on of the themes.
3. Add some demo pages from the examplePage of the theme
4. Push it to your reposistories (for instance on GitHub)

## What's the difference

1. The static page runs inside of a Container. It comes with a little webserver (NGINX)
2. The Docker registry on hub.docker.com is listening on changes in the master branch and build a new images with the current files automatically.
3. Watchertower checks for Docker images updates every 42 seconds. If there is a newer images available.
    1. It pulls the new image on the Docker host and
    2. it restarts the related running instances.

In this example [Watchtower](https://containrrr.github.io/watchtower/) is running on some server aslike the static webpage, but it can run on remote servers also. for more informations take a look on the [documentation](https://containrrr.github.io/watchtower//usage-overview/).
