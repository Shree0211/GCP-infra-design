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


