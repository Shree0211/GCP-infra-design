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
