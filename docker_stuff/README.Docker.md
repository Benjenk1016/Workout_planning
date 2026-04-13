### Building and running your application

When you're ready, start your application by running:
`docker compose -f docker_stuff/compose.yaml up --build`.

Stop the application by running :
`docker compose -f docker_stuff/compose.yaml down`

### Frontend hot reload workflow

The Compose setup uses a bind mount from your project folder into `/var/www/html`.
That means HTML, CSS, and PHP file edits on your machine are reflected immediately in
the running container (no image rebuild required for those changes).

Use this once to start:

`docker compose -f docker_stuff/compose.yaml up --build`

After that, keep it running and just refresh the browser after edits.

Rebuild only when you change container configuration (for example, `docker_stuff/Dockerfile`).

Your application will be available at http://localhost:8000.

### PHP extensions
If your application requires specific PHP extensions to run, they will need to be added to the Dockerfile. Follow the instructions and example in the Dockerfile to add them.

### Deploying your application to the cloud

First, build your image, e.g.: `docker build -t myapp .`.
If your cloud uses a different CPU architecture than your development
machine (e.g., you are on a Mac M1 and your cloud provider is amd64),
you'll want to build the image for that platform, e.g.:
`docker build --platform=linux/amd64 -t myapp .`.

Then, push it to your registry, e.g. `docker push myregistry.com/myapp`.

Consult Docker's [getting started](https://docs.docker.com/go/get-started-sharing/)
docs for more detail on building and pushing.