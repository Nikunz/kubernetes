# Deployment Configuration #

This README provides an overview of the Kubernetes deployment configuration defined in the provided YAML file. This configuration creates a deployment, a namespace, a resource quota, and a service for an Nginx application.

## Deployment

### Name: nginx
- The deployment is named "nginx" and is associated with the "nginx" app label.
- It is deployed in the "deployment-demo" namespace.
- It includes monitoring annotations with the value "true."

#### Deployment Specifications
- Replicas: 1
- Selector Label: "app: nginx"

#### Pod Template
- The pod template includes a container running the Nginx image.
- Container Name: nginx
- Container Ports:
  - Port 80 is exposed within the container.
- Resource Requests and Limits:
  - Requests:
    - CPU: 500 milliCPU (0.5 CPU cores)
    - Memory: 1Gi (1 gigabyte)
  - Limits:
    - CPU: 1000 milliCPU (1 CPU core)
    - Memory: 2Gi (2 gigabytes)

## Namespace

### Name: deployment-demo
- The namespace is named "deployment-demo" and has the label "apps: web-based."
- It includes an annotation with the key "type" and the value "demo."

## Resource Quota

### Name: mem-cpu-quota
- The resource quota is named "mem-cpu-quota" and is associated with the "deployment-demo" namespace.
- It sets resource limits and requests for CPU and memory.

#### Hard Limits
- Requests:
  - CPU: 4 CPU cores
  - Memory: 8Gi (8 gigabytes)
- Limits:
  - CPU: 8 CPU cores
  - Memory: 16Gi (16 gigabytes)

## Service

### Name: nginx
- The service is named "nginx" and is associated with the "nginx" app label.
- It is deployed in the "deployment-demo" namespace.
- It exposes port 80 of the Nginx deployment.

#### Service Specifications
- Ports:
  - NodePort: 30500
  - Port: 80
  - Protocol: TCP
  - TargetPort: 80
- Selector:
  - Selects pods with the label "app: nginx"

This Kubernetes configuration defines a deployment of Nginx within the "deployment-demo" namespace, enforces resource quotas, and exposes the Nginx service using a NodePort service type on port 30500. Adjust the resource requests and limits and other parameters as needed for your specific use case.
