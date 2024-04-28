# Deploying-backstage-on-docker

## Criando e Executando localmente o app backstage:

1 - Comando para criar o app:

```
npx @backstage/create-app@latest
```
![app_install](/Assets/app_install.png)


2- Executando o app localmente:

```
yarn dev 
```

![exec_local](/Assets/exe_local.png)

3- Gerar secret key:

```
$secret = [System.Convert]::ToBase64String([System.Text.Encoding]::UTF8.GetBytes((New-Guid).Guid))
$secret

```
![token](/Assets/gerar_token.png)

Nos arquivos app-config.yaml e no app-config.production.yaml:

```
 auth:
    keys:
      - secret: 'YWVlMjJhZjgtOTVmMC00ODQ0LWExZDUtNzJjNDMzYzQwMzcz'
```


## Executando com Kubernetes: 


1 - Build da imagem Docker:

![bulild](/Assets/image_build.png)

```
docker image build . -f packages/backend/Dockerfile --tag backstage:1.0.0
```

![docker_image](/Assets/imagem_no_docker.png)


2 - Habilitar o cluster Kubernetes no Docker Desktop:

![criar_cluster](/Assets/cluster_kubernetes.png)

![check_cluster](/Assets/check_cluster.png)


2 -  Deploy do postgres: 

2.1- Clonando repositório:

```
git clone https://github.com/guymenahem/how-to-devops-tools.git
```

Após clonar o repositório é necessário aplicar os arquivos de configuração do PostgreSQL com o kubectl.:

![config_postgrees](/Assets/config_postgrees.png)

