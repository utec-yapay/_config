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

jar files missing. Go to step 2
