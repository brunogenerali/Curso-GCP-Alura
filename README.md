# Provisionando uma aplicação

Projeto inicial tem como objetivo criar um servidor da aplicação web usando Compute Engine e um Cloud Storage com conteudo estático que poderá ser atualizado pelo DEV.

![Projeto Inicial](https://github.com/brunogenerali/images/blob/main/curso%20gcp%20alura/Projeto-inicial.png?raw=true)

Após evolução, será configurado 2 servidores com load balance

![Projeto evoluido](https://github.com/brunogenerali/images/blob/main/curso%20gcp%20alura/Projeto-evoluido.png?raw=true)

Realizado donwload de um site de teste para o projeto.

- Criado Instancia e instalado Apache2
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
- Alterando permissões de acesso das imagens



# Configurando IaC para o mesmo projeto

- Seguido documentação do Terraform para criação de GCP service account key pelo console para o projeto.  
