# Provisionando uma aplicação

## Aula 1 Provisionando uma aplicação

Projeto inicial tem como objetivo criar um servidor da aplicação web usando Compute Engine e um Cloud Storage com conteudo estático que poderá ser atualizado pelo DEV.

![Projeto Inicial](https://github.com/brunogenerali/images/blob/main/curso%20gcp%20alura/Projeto-inicial.png?raw=true)

Após evolução, será configurado 2 servidores com load balance

![Projeto evoluido](https://github.com/brunogenerali/images/blob/main/curso%20gcp%20alura/Projeto-evoluido.png?raw=true)

- Criar um novo projeto  
- Ativar o Compute Engine  
- Criar um nova instancia do tipo e2.micro

## Aula 2 e 3  

Realizado donwload de um site de teste para o projeto.

- Instalar Apache2
- Configurado Chave SSH para acesso a instancia
- Criando Cloud Storage para adicionar o conteudo do site.
- Instalar google cloud CLI
- Executar comanto de configuração
`gcloud init`  
Para alterar as configurações padrões definidas no init utilizar o comando  
`gcloud help config`  
Para adicionar outras configurações para trabalhar com multiplos projeto utilizar comando  
`gcloud topic configurations`  
- Copiando os arquivos do site para o bucket do gcp  
`gsutil -m cp -r {PATH Local} {PATH DO BUCKET}`  
- Alterando permissões de acesso das imagens para publico
`gsutil -m acl -r ch -u AllUsers:R {PATH BUCKET}`
- Copiando arquivos de maneira incremental  
`gsutil -m rsync {PATH LOCAL} {PATH DO BUCKET}`
- Criar script de atualização de arquivos  

## Aula 4 - Escalando o Site

### Criando Imagem  

Antes de criar uma imagem o ideal é parar a instancia.  

- Listar Instancias criadas  
`gcloud compute instances list`
- Para Instancia  
`gcloud compute instaces stop {INSTANCE NAME}`  
- Criar imagem da instancia  
`glcoud compute images create {IMAGE NAME} --source-disk {INSTANCE NAME}`
- Visualisar as imagens do GCloud  
`gcloud compute images list`  

### Template e instance group

- A partir da imagem criada, criar um instance template  
- Depois Criar um instance group com o template criado antes  
- Habilidar o Auto Scaling  selecionando o mínimo e o máximo de VMs e a imagem criada

## Aula 5 Alta Disponibilidade

Para o a escalabilidade automatica pode ser acessada por um unico IP deve-se utilizar um load Balance

- Reservar um IP Externo Estático  
- VPC Network > External IP Address  
- Reserve a Static Address (Caso reservado e não utilizado, será cobrado)  
- Para criar o Load Balance: Network Services > Load Balancing  
- Em Backend configuration criar um Health Check  
- Ajustar e testar as regras de firewall: VPC Network > Firewall Rules  

## EXTRAS

### Configurando IaC para o mesmo projeto

- Seguido documentação do Terraform para criação de GCP service account key pelo console para o projeto.  
