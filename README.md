
RideShare App
Technologies used - AWS, REST, Python, Docker, Load-Balancing, Zookeeper, Rabbitmq

To run:
  1. Create three AWS instances
  2. Place each of the zipfiles into the instances one by one.
  3. Unzip the files.
  4. In each instance, run the following commands:
```
    sudo docker-compose up
```
      --incase docker-compose up is not installed:
      ```
          sudo apt-get update
          sudo apt-get install docker
          sudo apt-get install docker-compose
      ```
  5. Loadbalancer set up:
  ```
    i.    Create two target groups using AWS.
    ii.   Assign the rides and users instances each to a separate target group.
    iii.  Create the load-balancer using the AWS tab found on the right-hand side.
    iv.   Assign the loadbalancer to the target group rides.
    v.    Now within the load balancer, go to Listeners -> Rules
    vi.   Edit the rules and add the following rules:
              IF /api/v1/users GOTO UsersInstance
              ELSE GOTO RidesInstance
  ```
  6. Also, ensure that port 80 for all three instances are exposed. Configure as per requirement using security groups.
  7. Once all three instances are up and load balancer is active, open Postman and send requests the orchestrator's IP address.
  
  
Further Enhancements:
  1. Could have added Master-election.
  2. Could have created and destroyed slaves as per requirement dynamically.

