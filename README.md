> **THIS REPO IS SEEDED FROM 2021 CODE AND AS SUCH CURRENTLY NEEDS MODERNISATION!** (see also [SEEDING.md](SEEDING.md).)



Python programs to publish messages onto RM.Field Rabbit MQ and track the message consumption by JobserviceV4 service.

Message simulator and load generator for performance testing of JobserviceV4.


This python toolset does the following :

1) Creates sample messages with unique caseIds without any database or datastores.
2) The number of messages to create is configured (Config.CASES_TO_FETCH).
3) The fixed number of messages are published onto RM.Field queue on RabbitMQ instance configured in (Config.RABBITMQ_HOST).
4) Publish messages onto RM.Field queue on RabbitMQ. 
5) Tracks the message consumption by Jobservice V4. 
6) Calculate and reports the message consumption rate.
''

Programs :

1) publish_create.py  : Generates 'Create' type messages and simulates the behaviour.
2) publish_cancel.py  : Simulates the behaviour of 'Create' followed by 'Cancel' . Generates 'Create' type messages followed by 'Cancel' messages .
3) publish_update.py  : Simulates the behaviour of 'Create' followed by 'Update'. Generates 'Create' type messages followed by 'Update' messages . 
4) testFiles.py 	  : Tracks message consumption and reports message consumption / processing rate.


GCP Deployment:

Dockerfile to build the docker image
create-perftests-pod.yml to create fwmtg-perf-test are included in the Python folder

How to run :

1) fwmtg-perf-tests deployment includes all the python scripts listed above.
2) Download the Makefile locally (local pc).
	make python 	  : Creates fixed number of 'Create' messages and publishes onto the RabbitMQ.
	make consume      : Tracks the message consumption by JObservicev4.
	make report 	  : Creates report with caseIds and message consumption rate.
	make clean		  : Removes all the txt files ( does not remove scripts).

Expected results :

Total processing time for 10000 number of requests is 157.970s.
Average processing time for 10000 number of requests is 75170.003ms  / 75.170s.
Number of requests per second are 63.
