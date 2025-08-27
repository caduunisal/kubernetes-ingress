Kubernetes Ingress

Este repositório contém um exemplo simples de como expor três páginas web estáticas em um cluster Kubernetes usando Deployments, Services e Ingress (NGINX).

📂 Estrutura do Repositório
.
├── home/
│   ├── index.html
│   ├── assets/
│   └── Dockerfile
├── about/
│   ├── index.html
│   ├── assets/
│   └── Dockerfile
├── contact/
│   ├── index.html
│   ├── assets/
│   └── Dockerfile
└── k8s/
    ├── deployments/
    │   ├── home.yaml
    │   ├── about.yaml
    │   └── contact.yaml
    ├── services/
    │   ├── home-svc.yaml
    │   ├── about-svc.yaml
    │   └── contact-svc.yaml
    └── ingress.yaml

🚀 Passo a Passo
1. Construir e publicar as imagens Docker

Cada pasta (home/, about/, contact/) possui um Dockerfile.
Exemplo de build e push:

docker build -t caduunisal/meusite-home ./home
docker push caduunisal/meusite-home

docker build -t caduunisal/meusite-about ./about
docker push caduunisal/meusite-about

docker build -t caduunisal/meusite-contact ./contact
docker push caduunisal/meusite-contact

2. Aplicar os manifests no Kubernetes
kubectl apply -f k8s/deployments/
kubectl apply -f k8s/services/
kubectl apply -f k8s/ingress.yaml

3. Ajustar o /etc/hosts

Adicione o domínio escolhido apontando para o IP do Ingress Controller (NGINX).

<IP_INGRESS_CONTROLLER> meusite.local

4. Testar

Abra no navegador:

http://meusite.local/
 → Página Home

http://meusite.local/about
 → Página About

http://meusite.local/contact
 → Página Contact

🛠 Tecnologias utilizadas

Kubernetes (Deployments, Services, Ingress)

NGINX como servidor web e Ingress Controller

Docker para empacotar os sites
