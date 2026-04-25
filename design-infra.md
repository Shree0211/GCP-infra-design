** Infrastructure Design Explanation **

* Compute Choice (GKE / Compute Engine / Cloud Run)

In our case we will use Cloud Run. Because of the following reasons:-
- Fully manages serverless platform
- Automatic scaling
- No server or Kubernetes management is required]
- Cost Effectice

* Why not GKE?
- GKE introduces Kubernetes operational which is unnecessary for single Spring Boot Service.

* Why not Compute Engine?
- Compute Engine requires manual instance management, scaling setup,
and patch management which increases operational effort in our case.

----------------------------------------------------------------------------------------

* Database Choice (MongoDB)

MongoDB will be hosted using MongoDB Atlas instead of self-managed
MongoDB instances.

* Why MongoDB Atlas?
- Fully managed database service
- Automated backups and patching
- Built-in replication and high availability

Cloud Run service will securely connect to MongoDB Atlas using
private networking and database credentials stored in Secret Manager

-----------------------------------------------------------------------------

* VPC Networking Design

* Cloud Run - Cloud Run will connect to the VPC using a Serverless VPC Connector
* Ingress Configuration - External users will access the application through a HTTPS Load Balancer.
* Database Connectivity -It will be in the private subnet. Only the application service will be allowed
to communicate with the database.

-----------------------------------------------------------------------------

* Secrets & IAM Design

* Secrets Management
- Application secrets such as MongoDB connection strings, API keys, and authentication credentials will be stored in Google Cloud Secret Manager.

* IAM 
- A service account will be created for the Cloud Run service of least privilege.
- The service account will only have permission to access required secrets from Secret Manager.

-----------------------------------------------------------------------------

* Logging and Monitoring

Application and infrastructure logs will be automatically collected using Google Cloud Operations Suite.

Logs include:
- application logs
- request logs
- error events
- deployment logs

Monitoring
Cloud Monitoring will track service health using metrics such as:
- request latency
- error rate
- instance scaling

Alerting
Alerts can be created and configured to notify the user and team in case of
- High CPU/memory usage
- service downtime
- increased error rates

Observability
Logs can be exported to Splunk for centralized monitoring,
dashboard creation, and incident analysis
