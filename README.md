### Miniconda 3 with Azure Functions
This sample is working for Miniconda 3 on Python 3.7 in Azure Functions V3 Host

### Walkthrough
Please follow the steps to build a docker custom image with Azure Functions:
1. Export Anaconda environment and place it into your function app project
    - `conda env export --from-history > environment.yml`
    - `cp ./environment.yml ./your/functionapp/project/`
2. Copy the Dockerfile into your function app project
    - `cp ./Dockerfile ./your/functionapp/project`
3. Build the custom Docker image
    - `docker build --no-cache --tag docker_org/image_name:tag .`
4. You can test the image locally
    - `docker run -p 8081:80  docker_org/image_name:tag`
    - `curl http://localhost:8081/api/HttpTrigger`
5. Upload your image into docker registry and create an Azure Functions App Service plan to host this custom image
