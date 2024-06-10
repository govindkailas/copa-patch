# copa-patch
The idea of this project started as a discussion here https://github.com/project-copacetic/copacetic/discussions/354#discussion-5708891. 

Everything will run in Kubernetes natively, the container images will be scanned used Trivy and the output json will be passed to copa. Copa is capable of patching the vulnerabilities in the container images.

Copa need buildkit as a depedency to build and patch the image. 
Copa can be run as a kubernetes deployment using this image, ghcr.io/project-copacetic/copa-action:v0.6.2.

## Workflow
1. Call the copa-patch service which is exposed as a LoadBalancer in Kubernetes with the container registry image URL.
2. The copa-patch service will pass the image to Trivy service and get the scanned report as a json.
3. The json will be passed to copa and copa patch the vulnerabilities and save the patched image.
4. patched image will be pushed to the container registry.