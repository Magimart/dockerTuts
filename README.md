# To run mongo db container 
docker run mongo   <!-- this will run and floods the terminal meaning not logging out, Better to run in detatched mode like below -->
# docker run -d --name mongoDB mongo 
docker container inspect mongoDb  <!-- inspect the mongo container we started for great commands  -->

under Networking setting you will find "IPAddress": "172.17.0.2",
replace the connection string in  the appjs file with ip address like below
eg   'mongodb://172.17.0.2:27017/mymongodb',
then build the image again
docker build -t mongodb-app .
docker run -d -p 4000:80 --name mongoDbv1 mongodb-app
# Now we check docker run we see two containers running
docker ps
should see below
PS Z:\nodes\myTutorials\docker\dockerAppMongoDB> docker ps
CONTAINER ID   IMAGE         COMMAND                  CREATED              STATUS              PORTS                    NAMES
2575365b3107   mongodb-app   "docker-entrypoint.s…"   About a minute ago   Up About a minute   0.0.0.0:3000->4000/tcp   mongoDbv1
6903f4a94373   mongo         "docker-entrypoint.s…"   25 minutes ago       Up 25 minutes       27017/tcp                mongoDb
PS Z:\nodes\myTutorials\docker\dockerAppMongoDB> 
# From the above you will see two containers running
one the mongo image container from docker hub
second is the our app container running on our host machine

# from the above we are running two containers mongo container and app container (mongodb-app)
docker build -t mongodb-app .
docker run -d -p 4000:80 --name mongoDbv1 mongodb-app
request at postman
get request http://localhost:4000/favorites
post request http://localhost:4000/favorites
mock data
{
   "name": "A new Hope",
   "type": "movie",
   "url": "http://swapi.dev/api/films/1/"
}
// From thses we will now try to multiple containers with each talking to each other via the 
Network. Keep learning :)












