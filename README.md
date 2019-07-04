# _config

This repository contains the docker-compose configuration file that sets up the whole YaPay infrastructure, together with the helper servers (dummy_*) that make a demo of the project possible.

To run the infrastructure, first make sure that all the repositories in the group ```utec-yapay``` are children of the same root directory. Then, ```cd``` to ```_config``` and run

```sudo docker-compose build```

to build the containers and

```sudo docker-compose up```
  
to start the services.
