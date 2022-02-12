## For ERPNext User:

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
#### Ubuntu: create a new user then add to docker group, then open new project folder...
- `sudo adduser frappe`
- `su - frappe`
- `mkdir frappe_docker`
- `cd frappe_docker`
- `git clone https://github.com/chiajunshen/shrdc_custom_frappe_docker.git`


1. Clone this repo in a directory of your choice
- `git clone <url of this repo>`

2. Navigate into the `shrdc_custom_frappe_docker` directory
- `cd shrdc_custom_frappe_docker`

3. Copy environment variables from the `env-example` file.
- `cp env-example .env` talk about the variable that can be changed...

4. Start all the docker containers. Note: Replace `<project_name>` to your preference.
- `docker-compose --project-name <project_name> up -d`

5. Monitor the site creation progress by logging the `<project_name>_site-creator_1` container.
- `docker logs <project_name>_site-creator_1 -f`

6. After the `<project_name>_site-creator_1` container exited, you can access ERPNext via `mysite.localhost` or whatever you have set in the `.env` file.



## For Developer (get this done asap):

### 1. Introduction

- Fork this repo to build your own image with ERPNext and list of custom Frappe apps.
- Change `nginx/Dockerfile` and add required apps. Refer comments in the file.
- Change `worker/Dockerfile` and add required apps.

Example file uses following apps:

- https://github.com/chiajunshen/shrdc_frappe_metabase
- https://github.com/chiajunshen/shrdc_bench_manager
- https://github.com/chiajunshen/shrdc_erpnext_telegram
- https://github.com/Drayang/ERPNext-Frepple
- https://github.com/leexy0/barcode_shrdc
- https://github.com/msf4-0/ERPNext_my_custom__maintenance

### 2. Build images

Execute from root of app repo

For nginx:

```shell
# For version-12
docker build --build-arg=FRAPPE_BRANCH=version-12 --build-arg=GITHUB_OWNER=<github-username> -t custom-erpnext-nginx:v12 nginx

# Example:
docker build --build-arg=FRAPPE_BRANCH=version-12 --build-arg=GITHUB_OWNER=chiajunshen -t custom-erpnext-nginx:version-12 nginx
```

For worker:

```shell
# For version-12
docker build --build-arg=FRAPPE_BRANCH=version-12 --build-arg=GITHUB_OWNER=<github-username> -t custom-erpnext-worker:version-12 worker

# Example:
docker build --build-arg=FRAPPE_BRANCH=version-12 --build-arg=GITHUB_OWNER=chiajunshen -t custom-erpnext-worker:version-12 worker
```

### 3. Push images to Docker Hub
may face `denied: requested access to the resource is denied` error
Execute from root of app repo: `docker login` log into the Docker Hub in which you want to push the images to

### 4. Configure `env-example`
change DOCKER_USERNAME to the username of the Docker Hub in which you have pushed to images to
