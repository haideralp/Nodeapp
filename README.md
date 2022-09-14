#### Building An Image for Node App

- Create a micro-service for node-app
- Create a dockerfile inside your app folder
- Create a script to package our node app in an iumage
- Create a container of our image
- Should load it on port 3000 or 80.
- Push it to docker up.

### 

```yaml
version: "3.9"  
services:              #defining the services as in containers that needs be summoned using this task. 
  mongodb:
    container_name: mongodb   #naming my container here
    image: mongo:latest
    ports:
      - 27017:27017
    restart: always
    volumes:
      - ./mongod.conf:/etc/mongod.conf  # specifying volumes for mongodconf file. 
     
  
  app:
    container_name: nodeapp
    restart: always
    build: ./app/Dockerfile # defining path  where to build from (location of docker file)
    image: haideralp/nodeapp # image naming convention 
    ports:
      - 3000:3000  #Specifying ports on which app needs to run on.
    depends_on: 
      - mongodb #giving condition that app is dependent on service mongodb running successfully. 
    environment:
      DB_HOST: mongodb://mongodb:27017     #setting of environment variables in the app.
    command: node app seeds/seed.js   # executing commands to fetch data. 
    # 
   ``` 