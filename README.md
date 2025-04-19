I have tested how to implement a DevOps workflow in Google Cloud.
First I created a GKE cluster to run a sample Go application and a git repository to host my code base. 
Then created Cloud Build Triggers, modified the code and the templates, and pushed updates to the repo that created for my first development and production application builds. 
Then pushed updates to the application to create new builds, and rolled back the production application to a previous version.
