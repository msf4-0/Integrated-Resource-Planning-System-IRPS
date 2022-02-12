Target:
- ERPNext
- Metabase Integration
- Telegram Integration
- shrdc_barcode
- Frepple Integration
- shrdc_cmms
- Build a perfect image (expose mariadb port for Metabase)
- Improve on Setup documentation

### SHRDC Custom Frappe Docker
- Prerequisites: Docker Engine, Docker Compose
- Frappe Apps included: ERPNext, Metabase Integration.

### Setup
1. Clone this repo in a directory of your choice
- `git clone <url of this repo>`

2. Navigate into the `shrdc_custom_frappe_docker` directory
- `cd shrdc_custom_frappe_docker`

3. Copy environment variables from the `env-example` file.
- `cp env-example .env`

4. Start all the docker containers. Note: Replace `<project_name>` to your preference.
- `docker-compose --project-name <project_name> up -d`

5. Monitor the site creation progress by logging the `<project_name>_site-creator_1` container.
- `docker logs <project_name>_site-creator_1 -f`

6. After the `<project_name>_site-creator_1` container exited, you can access ERPNext via `mysite.localhost` or whatever you have set in the `.env` file.



### For Developer:

### Introduction

- Fork this repo to build your own image with ERPNext and list of custom Frappe apps.
- Change `nginx/Dockerfile` and add required apps. Refer comments in the file.
- Change `worker/Dockerfile` and add required apps.

Example file uses following apps:

- https://github.com/pipech/frappe-metabase

### Build images

Execute from root of app repo

For nginx:

```shell
# For edge
docker build -t custom-erpnext-nginx:latest nginx

# For version-12
docker build --build-arg=FRAPPE_BRANCH=version-12 -t custom-erpnext-nginx:v12 nginx
```

For worker:

```shell
# For version-12
docker build --build-arg=FRAPPE_BRANCH=version-12 --build-arg=GITHUB_OWNER=<github-username> -t custom-erpnext-worker:version-12 worker

# Example:
docker build --build-arg=FRAPPE_BRANCH=version-12 --build-arg=GITHUB_OWNER=chiajunshen -t custom-erpnext-worker:version-12 worker

```
