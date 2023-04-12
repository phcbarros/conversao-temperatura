# Projeto conversão de temperatura

### Sobre o projeto
O projeto conversão de temperatura é um projeto desenvolvido em NodeJS. O projeto tem como objetivo ser um exemplo para a criação de ambiente com containers usando NodeJS.

### Observações do projeto
A aplicação é exposta usando a porta 8080

### Comandos

```bash
# criar cluster
k3d cluster create meucluster -p "80:30000@loadbalancer"

# criar/atualizar o deployment (dentro da pasta k8s)
kubectl apply -f ./deployment.yaml

# deletar cluster
k3d cluster delete meucluster  
```