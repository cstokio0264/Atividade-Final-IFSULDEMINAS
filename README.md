# CONTÊINERES DOCKER PARA A IMPLEMENTAÇÃO DE UM AMBIENTE DE     CLIENTE E SERVIDOR

# Cássio Sousa dos Santos

# Palavras-chave: Docker, Contêineres, Cliente, Servidor.


# 1 INTRODUÇÃO

Este relatório acadêmico abordará o processo de criação e configuração de contêineres Docker para a implementação de um ambiente de cliente e servidor. O objetivo é demonstrar detalhadamente o processo de criação de um contêiner para uma aplicação web e outro contêiner para fornecer uma interface gráfica usando o localhost na porta 8060. Isso permitirá o acesso através do navegador do hospedeiro ao host cliente, que será um sistema operacional Ubuntu com o navegador Mozilla Firefox instalado.
Vale lembrar que o contêiner criado para o nosso servidor de aplicação web estará acessível apenas aos clientes da rede à qual o servidor está conectado. Como a intenção do projeto é detalhar cada etapa do processo, desde a configuração inicial até a execução dos contêineres, destacando as vantagens e desafios encontrados ao utilizar Docker para criar ambientes de servidor e cliente integrados, não iremos nos aprofundar no contexto de disponibilização da aplicação web na internet. Portanto, o contêiner com o servidor de aplicação web estará disponível apenas aos clientes conectados à rede interna privada com IP da rede 192.168.2.0, sendo o seu acesso através do IP do servidor 192.168.2.67:80.
# 2 SOFTWARE UTILIZADOS

1.	Docker
Docker é uma plataforma de software que permite criar, testar e implantar aplicações rapidamente dentro de contêineres. Contêineres são leves e incluem tudo o que a aplicação necessita para rodar.
•	Download e instalação: Baixe o Docker Desktop aqui e siga as instruções de instalação.
•	Configuração: Após a instalação, inicie o Docker Desktop. Ele irá rodar um terminal na bandeja do sistema, indicando que está pronto para uso.
2.	Visual Studio Code (VS Code)
VS Code é um editor de código-fonte leve e poderoso, que oferece suporte a diversas linguagens de programação e funcionalidades de depuração integradas.
Passos para Instalação do VS Code:
•	Download e instalação: Baixe o Visual Studio Code aqui e siga as instruções de instalação.
•	Extensão Docker: Após a instalação do VS Code, instale a extensão Docker para facilitar a criação e gerenciamento de contêineres diretamente do editor.

# 3 DOCKERFILE E CRIAÇÃO DA IMAGEM DO SERVIDOR WEB

Um Dockerfile é um script contendo uma série de instruções sobre como construir uma imagem Docker. Para este projeto, criaremos uma imagem de um sistema operacional Ubuntu com o servidor web Apache instalado. Uma imagem de contêiner é um pacote padronizado que inclui todos os arquivos, binários, bibliotecas e configurações para executar um contêiner.
Abra o arquivo Dockerfile e escreva o script da seguinte forma:
 
1.	Para gerar a imagem com o dockerfile, abra o terminal do VS code e execute o comando: docker image build -t ubuntu-apache:1.0 .
 

2.	Execute o Contêiner
Se o contêiner estiver em execução, você verá suas informações listadas no comando docker ps. Caso contrário, você pode usar docker ps -a para listar todos os contêineres, incluindo os que não estão em execução.
 

# 4 IMAGEM DO DOCKER HUB PARA A CONSTRUÇÃO DO AMBIENTE VIRTUAL CLIENTE 

	Para obter a imagem que será usada na criação do container com ambiente virtual cliente, optaremos por baixar uma imagem disponível no Docker Hub através do link.



1.	Primeiro, extraia a imagem do Docker Hub usando o comando:
docker pull dorowu/ubuntu-desktop-lxde-v nc
2.	Depois que a imagem for baixada, podemos criar o contêiner a partir dela usando o comando:
docker run -p 6080:80 -v /dev/shm:/dev/shm --name meuCliente dorowu/ubuntu-desktop-lxde-vnc

Este comando cria e inicia um contêiner chamado meuCliente, que executa a imagem dorowu/ubuntu-desktop-lxde-vnc, com a porta 6080 do host mapeada para a porta 80 do contêiner e o diretório /dev/shm montado para otimização de desempenho.

 
# 5 APLICAÇÃO WEB

	Esta aplicação web da Pokédex foi desenvolvida usando HTML, CSS e JavaScript, permitindo aos usuários acessarem informações sobre os 151 Pokémon originais. A estrutura do código inclui HTML para marcar e estruturar o conteúdo, CSS para estilização e JavaScript para interatividade. Essa combinação de tecnologias garante uma aplicação web interativa, fácil de atualizar e manter, com todas as vantagens de isolamento e portabilidade oferecidas pelo Docker.

 
# 6 CONSIDERAÇÕES FINAIS
	O principal objetivo deste trabalho foi explorar o uso do Docker e do Visual Studio Code (VS Code) para a criação e implantação de aplicações dentro de contêineres. Além disso, visou-se a construção de um servidor web e de um ambiente virtual cliente para acesso a aplicação web utilizando contêineres Docker, para demonstrar a versatilidade e eficiência dessas tecnologias.
	A metodologia adotada incluiu a utilização de duas ferramentas de software principais: Docker e Visual Studio Code. O Docker foi escolhido por sua capacidade de criar ambientes isolados e leves que contêm tudo o que uma aplicação precisa para ser executada. A instalação e configuração do Docker Desktop permitiram o gerenciamento de contêineres de forma eficiente. O Visual Studio Code, por sua vez, foi selecionado por ser um editor de código-fonte robusto, com suporte a diversas linguagens de programação e funcionalidades de depuração integradas. A extensão Docker no VS Code facilitou a criação e gerenciamento de contêineres diretamente do editor.
	Para a criação do servidor web, foi desenvolvido um Dockerfile, um script que contém as instruções para construir uma imagem Docker. Este Dockerfile especificava um sistema operacional Ubuntu com o servidor web Apache instalado. Após a construção da imagem, foi possível executar um contêiner a partir desta imagem, disponibilizando o serviço de servidor web.
	Adicionalmente, uma imagem do Docker Hub foi utilizada para a construção do ambiente virtual cliente. Esta imagem foi baixada e um contêiner foi criado a partir dela, mapeando portas do host para o contêiner e otimizando o desempenho através de diretórios montados.
	Os principais resultados incluem a criação bem-sucedida de um contêiner de servidor web funcional e de um ambiente virtual cliente, ambos utilizando Docker. Estes resultados são significativos pois demonstram a capacidade do Docker de simplificar a implantação e gestão de aplicações em ambientes isolados. A utilização de contêineres permite uma maior portabilidade das aplicações, facilita o escalonamento e contribui para a consistência entre ambientes de desenvolvimento e produção.
Em suma, o trabalho evidencia a importância do Docker e do Visual Studio Code como ferramentas essenciais para desenvolvedores que buscam agilidade e eficiência na criação e gestão de aplicações. A metodologia utilizada e os resultados obtidos reforçam a relevância dessas tecnologias no cenário atual de desenvolvimento de software.

# 7 REFERÊNCIAS

DOCKER INC. Docker Documentation. 2023. Disponível em: https://docs.docker.com/. Acessado em 10/10/2024.

MICROSOFT. Visual Studio Code Documentation. 2023. Disponível em: https://code.visualstudio.com/docs. Acessado em 10/10/2024.

W3SCHOOLS. HTML, CSS, JavaScript Tutorials. 2023. Disponível em: https://www.w3schools.com/. Acessado em 10/10/2024.

DIGITAL INNOVATION ONE. js-developer-pokedex. Repositório GitHub. 2023. Disponível em: https://github.com/digitalinnovationone/js-developer-pokedex. Acessado em 14/10/2024.

VASCONCELOS, João P.; SILVA, Maria L. Docker para Desenvolvedores. Editora TechBooks, 2020.
