# .Net Web App Containerization and Deployment
This is a mock example of a .NET Web App with database connectivity, packaged, containerized and deployed using Docker
The script below deploys a .Net Pet shop web application published in 2008 initially as a reference to the .NET 2 release and how development works, as well as a database for the products.
It is a pure example of containerization using Docker and deployment of old .NET apps using Microsoft Server Core 2019

ls ./petshop/web
docker build -t petshop-web ./petshop/web
// Running a container with -d arg makes it detached, when we close the project the container will also be removed automatically
docker run -d -P --name web petshop-web

// This image was pulled from the Docker Hub, an image which integrates the database required for the web app to pull the objects
docker run -d -p 1433:1433 --name petshop-db psdockernetfx/petshop-db

// To test the connectivity, simply enter the site to see if it works properly, but solely for the database connectivity you can ping to see if the host receives communication from it
docker exec web ping petshop-db