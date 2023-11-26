# Docker Compose with Traefik
Este repositório contém configurações Docker Compose para usar o Traefik como proxy reverso em um ambiente Docker. O proxy reverso facilita a exposição de serviços locais e fornece recursos avançados, como balanceamento de carga e SSL.

## Pré-Requisitos
Certifique-se de que você tenha o Docker e o Docker Compose instalados em sua máquina antes de prosseguir. Você pode encontrar informações sobre como instalá-los nos seguintes links:

- [Docker Installation Guide](https://docs.docker.com/get-docker/)
- [Docker Compose Installation Guide](https://docs.docker.com/compose/install/)

## Como Usar
### 1. Clone o Repositório
```bash
git clone https://github.com/moresrc/docker-compose-traefik.git
cd docker-compose-traefik
```

### 2. Crie a Rede Docker
Certifique-se de ter uma rede Docker chamada "traefik" criada para garantir que os containers que serão executados possam se comunicar uns com os outros de maneira eficiente e segura. Se não tiver, crie-a usando o comando a seguir:
```bash
docker network create traefik
```
### 3. Suba o Container do Traefik
Para iniciar o Traefik execute o comando abaixo:
```bash
docker compose -f "traefik-docker-compose.yaml" up -d
```
Certifique-se de que o container do Traefik está em execução antes de prosseguir.

### 4. Escolha o Serviço para Subir
Para subir um serviço, basta executar o comando anterior substituindo o nome do arquivo yaml pelo serviço que desejamos utilizar. Para subir o serviço do [whoami](https://github.com/traefik/whoami), por exemplo, basta executar:
```bash
docker compose -f "whoami-docker-compose.yaml" up -d
```

### 5. Acesse Seus Serviços
Cada serviço pode ser acessado pelo navegador usando o endereço `http://*.docker.localhost`, onde `*` geralmente é o nome do serviço em questão ou algo que remeta a ele. Caso deseje personalizar o endereço de acesso para um serviço específico, ajuste as labels nos arquivos YAML de cada serviço, reinicie o serviço e, em seguida, acesse-o pelo novo endereço configurado.