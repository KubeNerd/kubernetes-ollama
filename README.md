# Ollama Deployment on Kubernetes

Este repositório contém os arquivos e instruções necessários para implementar o Ollama em um cluster Kubernetes utilizando MicroK8s. O deployment utiliza NGINX Ingress Controller para expor o serviço.

## Pré-requisitos

- Kubernetes (MicroK8s)
- Helm
- NGINX Ingress Controller instalado no cluster
- Configuração de um namespace `ollama`

## Estrutura dos Arquivos

- `deployment.yaml`: Configuração do Deployment do Ollama
- `service.yaml`: Configuração do Service para o Ollama
- `ingress.yaml`: Configuração do Ingress para expor o Ollama
- `README.md`: Instruções de implementação

## Deployment

### Deployment

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: ollama
  namespace: ollama
spec:
  replicas: 1
  selector:
    matchLabels:
      app: ollama
  template:
    metadata:
      labels:
        app: ollama
    spec:
      containers:
      - name: ollama
        image: ollama/ollama:latest
        ports:
        - containerPort: 11434
