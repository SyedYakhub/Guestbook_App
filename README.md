# Guestbook_App

Deploy Guest Book App on Kubernetes

Step 1: Understand the Task
The task is about deploying a guestbook application on a Kubernetes cluster. The application has two tiers: a back-end tier with Redis master and slave deployments, and a front-end tier with a PHP-based application. The back-end tier consists of two deployments with specific replica counts, CPU and memory requests, and container images. The front-end tier also has a deployment with replicas, resource requests, and a container image. Services need to be created for both Redis and the front-end application with specific port configurations.

Step 2: Purpose of the Task
The purpose of this task is to deploy the guestbook application on the Kubernetes cluster using specific configurations for the Redis master and slave deployments, as well as the front-end application. By deploying the application in this way, it will be able to manage entries for guests and visitors efficiently, using Redis for data storage.

Step 3: Steps to Accomplish the Task
Here are the detailed steps to accomplish the task:

1. Create Redis Master Deployment:
   - Name: redis-master
   - Replicas: 1
   - Container Name: master-redis-nautilus
   - Image: redis
   - CPU Request: 100m
   - Memory Request: 100Mi
   - Container Port: 6379

2. Create Redis Master Service:
   - Name: redis-master
   - Port: 6379
   - TargetPort: 6379

3. Create Redis Slave Deployment:
   - Name: redis-slave
   - Replicas: 2
   - Container Name: slave-redis-nautilus
   - Image: gcr.io/google_samples/gb-redisslave:v3
   - CPU Request: 100m
   - Memory Request: 100Mi
   - Environment Variable: GET_HOSTS_FROM=dns
   - Container Port: 6379

4. Create Redis Slave Service:
   - Name: redis-slave
   - Port: 6379
   - TargetPort: 6379

5. Create Frontend Deployment:
   - Name: frontend
   - Replicas: 3
   - Container Name: php-redis-nautilus
   - Image: gcr.io/google-samples/gb-frontend:v4
   - CPU Request: 100m
   - Memory Request: 100Mi
   - Environment Variable: GET_HOSTS_FROM=dns
   - Container Port: 80

6. Create Frontend Service:
   - Name: frontend
   - Type: NodePort
   - Port: 80
   - NodePort: 30009

Once the above steps are completed, you can access the guestbook app by clicking on the "+" button in the top left corner and selecting "port to view on Host 1," then entering the nodePort (30009).

Remember, you can use any labels of your choice for the deployments and services.
