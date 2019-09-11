# _config

This repository contains the docker-compose configuration file that sets up the whole YaPay infrastructure, together with the helper servers (dummy_*) that make a demo of the project possible.

To run the infrastructure...
1. Make sure that all the repositories in the group `utec-yapay` are children of the same root directory.
2. `cd` to `yapay_backend/yapay-spring-boot` and run `mvn clean install` to create the `target` directory and package the project into jar files.
3. `cd` to `_config` and run  `sudo docker-compose build` to build the containers
4. `sudo docker-compose up` to start the services.

## Troubleshooting
```console
Step 2/3 : COPY target/*.jar app.jar
ERROR: Service 'backend' failed to build: COPY failed: no source files were specified
```
**Solution:** jar files missing. Go to step 2

```console
ERROR: for database  Cannot start service database: driver failed programming external connectivity on endpoint yapay_db (e6499a4caacf3fb9100ce578aa829f1df3401beca76fd04299dc46f8d4c05712): Error starting userland proxy: Bind for 0.0.0.0:5432 failed: port is already allocated
ERROR: Encountered errors while bringing up the project.
```
**Solution:** There's a process running on port 5432 (probably postgres) on your host.
Find information about the process in port 5432
```bash
ps -p $(sudo lsof -t -i tcp:5432) # MacOS
ps -p $(sudo lsof -t -i :5423 -s tcp:LISTEN) # Ubuntu
```
If it's indeed postgres, stop the database.
```
# MacOS
sudo su postgres
pg_ctl -D $DATADIRECTORY stop # $DATADIRECTORY could be `/Library/PostgreSQL/10/data`
```
