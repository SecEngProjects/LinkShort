# LinkShort - Containerised URL shortener

This is the Python code and Docker/Kubernetes configuration for a link shortening web app

**This is not a functional application yet:**

> I will make a full release on this repo when it is in a secure, production ready state

I am using this to learn:
- Docker & Kubernetes
- Python web app development
- DevSecOps automation

## Testing locally

- Create a file in the root directory, next to the `docker-compose.yaml` file, called `.env`, with the following contents, customising the values between **<>** with your own substitutions:
```txt
REDISUSER=default
REDISMASTER=<a-super-strong-password>
REDISREPLICA=<a-different-super-strong-password>
```

**! WARNING !**

> Please make sure your local environment variables in your terminal do not share names with the ones in this `.env` file.
- If you change the names of the variables in this file, make sure to change their references in the `docker-compose.yaml` file as well.

### Docker compose
- From root directory of repository, run this command:
```bash
docker-compose up --detach --scale redis-master=1 --scale redis-replica=3
```
```bash
[+] Running (6/6)
 ✔ Container linkshort-app-1
 ✔ Container linkshort-redis-replica-2
 ✔ Container linkshort-redis-replica-3
 ✔ Container linkshort-redis-replica-1
 ✔ Container linkshort-redis-master-1
 ✔ Network linkshort_ls-net
```

- If succesful, app will be running at [http://localhost:5000](http://localhost:5000), with a redis master database with 3 replica nodes.

- To shut down the service, run this command:
```bash
docker-compose down
```

## Application Features

- [x] Simple URL shortening capabilities for URLs
- [x] Sanitises input from user for both URLs and extensions on requests
- [x] Checks user input for URLs that begin with *HTTPS* only
- [ ] Checks submitted URLs for internet reputation before generating them, reject poor reputation URLs
- [x] Nice looking frontend with CSS and HTML
- [x] Handles errors gracefully, with 404 and 500 error pages rendered to the users
- [x] Containerised with docker compose using
- [ ] Kubernetes deployment configuration with database in stateful sets
- [ ] Demonstration application set up and deployed on cloud provider

### (Current features have a checkmark, planned ones do not)

## DevSecOps Automation

- [x] [Super Linter](https://github.com/super-linter/super-linter) Code linting for all languages on PRs
- [x] [Snyk](https://snyk.io) Automated security scanning and vulnerability patching
- [ ] [Renovate](https://www.mend.io/free-developer-tools/renovate/) Automated dependency upgrades
- [ ] [Commitizen](https://commitizen-tools.github.io/commitizen/) Commit standardisation

### (Current automations have a checkmark, planned ones do not)

## Developed by Jack
![Alt Text](https://raw.githubusercontent.com/jacksec/jacksec.github.io/master/assets/img/logo.png)

[My site](https://jacksec.engineer)
