# Module 1 Homework: Docker & SQL

## Question 1. Understanding docker first run

Run docker with the `python:3.12.8` image in an interactive mode, use the entrypoint `bash`.
What's the version of `pip` in the image?

**Answer:**
24.3.1

**Solution:**
Command used to find the version:
```bash
docker run -it python:3.12.8 bash
pip --version
# Output: pip 24.3.1 from /usr/local/lib/python3.12/site-packages/pip (python 3.12)
```

## Question 2. Understanding Docker networking and docker-compose

Given the `docker-compose.yaml`, what is the hostname and port that pgadmin should use to connect to the postgres database?

**Answer:**
db:5432

**Reasoning:**
1. **Hostname:** Inside the Docker network, services communicate using their service names defined in the YAML file. Here, the service is named `db`.
2. **Port:** We must use the **internal** container port (`5432`), not the external host port (`5433`). The mapping `5433:5432` is for external access (Host -> Container), but PgAdmin is running inside the same network (Container -> Container).