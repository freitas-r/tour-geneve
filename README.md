# tour-geneve

Documento Descritivo das Funcionalidades
“Notificações”, “Chat” e "Ajude seu Vizinho" versão 1.6


1.	Introdução

Este documento especifica requisitos da funcionalidade das “Notificações”, “Chat” e “Ajude seu Vizinho”, fornecendo aos desenvolvedores as informações necessárias para seu projeto e implementação.
O objetivo destas funcionalidades é ajudar em problemas e necessidades que podem surgir para os moradores, relativos à sua unidade habitacional, questões do dia a dia e que poderiam ser resolvidos com a ajuda de administradores ou de vizinhos, criando assim um ambiente colaborativo que facilite e melhore o convívio social do condomínio.

1.1	Visão geral do documento

Além desta seção introdutória, as seções seguintes estão organizadas como descrito abaixo.
Seção 2 – Descrição geral do sistema: apresenta uma visão geral do sistema, caracterizando qual é o seu escopo e descrevendo seus usuários.
Seção 3 – Arquitetura e tecnologias empregadas: especifica a arquitetura de banco de dados, linguagem utilizada em back-end, recursos de front-end e requisitos funcionais para o sistema.

1.2	Considerações iniciais

As soluções apresentadas consideram a existência de uma plataforma de gestão para condomínios, dotada de sistema web com aplicativo mobile e recursos de gestão financeira, portaria, cobranças, dentre outras, bem como sistema de usuário e senha para os moradores.


 ![Tela_Inicial](https://user-images.githubusercontent.com/60231582/155038862-29cb4fe1-349f-45d0-bcbf-b96e88685230.png)
 
Figura 1 - Como premissa inicial consideramos a existência de um sistema completo de gestão de condomínios. Fonte: https://apcontrole.com.br/

2.	Descrição geral das funcionalidades

2.1	Notificações

Para que as funcionalidades que serão aqui apresentadas cumpram o seu objetivo de forma plena, é necessário um sistema de notificações para alertar o usuário de mensagens recebidas de vizinhos (ver item 2.2 Chat) e quando um novo pedido de ajuda é publicado (ver item 2.3 Ajude seu Vizinho).
As notificações contemplam notificação “push” no aplicativo mobile e um e-mail para o usuário, de forma semelhante ao que ocorre em redes sociais.
Este sistema de notificações futuramente também servirá para outras finalidades, como alertar sobre faturas com vencimento próximo e avisos do condomínio.

 ![notifications](https://user-images.githubusercontent.com/60231582/155039004-75042e32-ec0a-413d-82c1-16fcdf94652a.png)

Figura 2 - Tela de notificações e notificações na tela de bloqueio do mobile. Fonte: autores.

2.2	Chat

A solução do chat integrada ao aplicativo visa facilitar o contato entre moradores, bem como entre morador e administração.
Possui finalidade de resolver questões diárias como avisar um vizinho que deixou os vidros do carro aberto, uma roupa que caiu do varal, dentre diversas situações vividas em um condomínio.
Os moradores ao receberem uma nova mensagem também recebem uma notificação através do aplicativo e/ou e-mail.
O chat também tem papel importante na funcionalidade “Ajude seu Vizinho” que será apresentada mais adiante neste capítulo, onde servirá como meio de contato entre o morador que requisitou o auxílio e aquele que deseja ajudar.

 ![chat](https://user-images.githubusercontent.com/60231582/155039084-ca6a57a3-d827-4b35-8434-97eab13fa380.png)

Figura 3 - Layout do chat. Fonte: autores.

2.2.1	Lista de contatos
Como parte da ferramenta de chat e com a finalidade de facilitar o contato entre condôminos e administração haverá a lista completa de contatos dos moradores e, em uma seção destacada, o contado da administração e síndico.
O contato direto com a administração visa ter um canal direto e possibilitar dirimir dúvidas, resolver questões financeiras, dentre outros. Para isso, o morador terá acesso aos contatos do síndico, responsável financeiro e funcionários que exercem papel de administração do condomínio.
Ao clicar em “ver todos os contatos”, uma lista com todos os inquilinos cadastrados do condomínio aparecerá, contendo nome, bloco (se houver) e número do apartamento.

2.3	Ajude seu Vizinho

Muitas vezes precisamos pendurar um quadro e não temos as ferramentas adequadas para realizar o serviço, mas um vizinho pode ter. Nesta solução o morador insere no sistema uma “demanda” de maneira análoga a uma ordem de serviço.
Existirão 2 possíveis fluxos para a criação da demanda no sistema, como será descrito a seguir. Em ambos os casos a demanda contemplará:
-As informações do usuário que a criou;
- Categoria estruturada de que tipo de serviço se refere através de opções dadas pelo próprio sistema (exemplo: Reformas e Reparos → Eletricista → Fiação Elétrica → Reparo na Fiação Elétrica); e
- Uma breve descrição da tarefa.
Portanto, a diferenciação dos subtópicos a seguir será focada no fluxo de cada um.

 ![figura_1](https://user-images.githubusercontent.com/60231582/155039259-5fe51c9d-1cf8-43b1-b38f-1e082180f1cf.png)

Figura 4 - Layout da aplicação Ajude seu Vizinho. Fonte: autores.

2.3.1	Demanda interna para os vizinhos
O usuário poderá escolher solicitar ajuda aos vizinhos e, no momento em que o usuário envia a demanda para o sistema, todos os moradores daquele condomínio recebem uma notificação pelo aplicativo e/ou um e-mail do pedido de ajuda. 
 Com isso, caso um morador possua as ferramentas e/ou a disponibilidade de ajudar seu vizinho, pode assumir a demanda e ela ficará auto atribuída a ele.
De forma geral, o funcionamento é semelhante a um sistema de gestão de manutenção, onde ordens de serviços são emitidas e atribuídas a operadores. Porém, neste caso, todos podem emitir demandas e todos podem ajudar a resolve-las.

2.3.2	Demanda para a plataforma GetNinjas
Mesmo que notificações sejam enviadas para todos os moradores, pode ser que ninguém possua as ferramentas ou a habilidade necessária para aquela demanda, o que frustraria o objetivo da funcionalidade que é ajudar a resolver problemas.
Deste modo, a funcionalidade terá uma integração com a plataforma “GetNinjas”, que conecta pessoas a prestadores de serviço, fornecendo orçamento em um curto espaço de tempo. A integração será através de uma API que transitará requisições dos moradores em formato de objeto de dados para a referida plataforma.
 
 ![getninjas](https://user-images.githubusercontent.com/60231582/155039283-69060863-07ee-46cc-b6bb-c4d8fc38c7d6.png)

Figura 5 - Página do GetNinjas. Fonte: https://www.getninjas.com.br/

Sendo a demanda encaminhada conforme o fluxo descrito em 2.3.1 (ou seja, de internamente ao condomínio), caso a mesma não seja atendida por um vizinho, após um determinado período de tempo será enviada uma solicitação de autorização ao usuário que gerou a demanda dando encaminhamento da mesma para a GetNinjas. 
A mesma estrutura de dados consumida pela plataforma GetNinjas será utilizada para gerar a demanda interna para os vizinhos (item 2.3.1). Assim, todas informações necessárias para a realização dos orçamentos já estarão prontas para serem encaminhadas através do envio e integração com a ferramenta.
Pensando na praticidade, urgência e até mesmo na privacidade, a partir de nossa funcionalidade o morador poderá enviar diretamente a demanda para a plataforma GetNinjas, e neste caso os vizinhos não serão notificados.

 ![fluxo ajude seu vizinho](https://user-images.githubusercontent.com/60231582/155039315-3e108b1c-721a-459d-849d-722ccc4d4bb6.png)

Figura 6 - Telas de cadastro de uma demanda. Fonte: autores.

3.	Arquitetura e Tecnologias empregadas

3.1	Arquitetura

O padrão de arquitetura de três camadas (3-Tier Architecture) foi escolhido para manter a organização e praticidade, já que cada camada executa sua própria infraestrutura, podendo se desenvolver cada camada simultaneamente, acelerando o processo de finalização da solução.
O padrão também é uma ótima opção pela segurança que fornece, já que a camada de dados não pode se comunicar diretamente com a camada de apresentação.
As camadas são:
 - Apresentação: Exibe e coleta informação.
 - Aplicativo: Camada lógica da aplicação.
 - Dados: Onde toda a parte back-end voltada para o banco de dados relacional acontece.

  ![arqte](https://user-images.githubusercontent.com/60231582/155039341-35190cb9-8c70-407b-b42b-d30b8691de24.png)

Figura 7 – Arquitetura de três camadas adotada pela equipe Tour Geneve. Fonte: autores.

3.2	Front-end

As interfaces com o usuário são de vital importância para o sucesso do sistema, principalmente por ser um sistema que será utilizado diariamente e por usuários de todas as faixas etárias. O sistema terá uma interface amigável ao usuário primário sem se tornar cansativa aos usuários mais experientes.
O Flutter é a tecnologia de front end escolhida pra ser utilizada pois é muito versátil, é um framework que abrange IOS e ANDROID com o mesmo código fonte e pela facilidade de consumir API's juntamente com o PHP. O Flutter possui muitas variações pra construção de UX e UI, além de possuir a linguagem POO Dart, que possibilita que reutilizemos componentes dentro do código e possamos utilizar o SOLID com mais facilidade.

3.3	Back-end

Para a linguagem de programação no lado do servidor (back-end) será utilizado a linguagem PHP para determinar as regras de negócio e PDO para a comunicação com o banco de dados.
A linguagem foi adotada por ser amplamente utilizada por desenvolvedores e é considerada fácil de aprender e manusear, código aberto, o que torna seu custo menor. Possui comunidade ativa, com sua última atualização da versão 8.1.3 realizada em 17/02/2022.
A linguagem PHP possui alto desempenho e é amplamente aceita em servidores que hospedam aplicações, como Hostgator e Hostinger. 
Será utilizado o paradigma de orientação a objetos como metodologia de construção do código, separando itens por classes de objetos (o modelo de atributos), as regras de negócio (controller) e as regras de serviço junto ao banco de dados (querys).

3.4	Banco de Dados

Para que a implementação das funcionalidades ocorra de forma fácil e não necessite grandes alterações no sistema existente, será utilizado banco de dados PostgreSQL com tabelas próprias (tb_chat, tb_demandas, por exemplo) no banco que se relacionarão com a tabela de usuários existentes (tb_moradores, por exemplo) de forma que o “id” do morador servirá como chave estrangeira. Desta forma, a relação será de um para muitos, podendo um id gerar diversos chats e demandas.
Da mesma forma, a tabela demanda se relacionará com o responsável pela execução através de uma tabela (tb_executantes, por exemplo) através de uma chave estrangeira, identificado se é através de moradores ou GetNinjas.

 ![diagrama1 1](https://user-images.githubusercontent.com/60231582/155039385-c11d49e5-80e5-44c2-af2f-1fd3f8b4ccd6.png)

Figura 8 - Diagrama do banco de dados. Fonte: autores.

3.5	Requisitos funcionais e não funcionais (RF e RNF)

Tabela 1 - RF0001, enviar mensagens no Chat.
Identificador	RF0001
Nome	Enviar mensagens
Módulo	Chat
Data de criação	19/02/2022	Autor	Tour Geneve
Data da última alteração	19/02/2022	Autor	Tour Geneve
Versão	01	Prioridade	Essencial
Descrição	Permite ao usuário enviar mensagens através do chat.

Tabela 2 - RF0002, receber mensagens no Chat.
Identificador	RF0002
Nome	Receber mensagens
Módulo	Chat
Data de criação	19/02/2022	Autor	Tour Geneve
Data da última alteração	19/02/2022	Autor	Tour Geneve
Versão	01	Prioridade	Essencial
Descrição	Permite ao usuário receber mensagens através do chat.

Tabela 3 - RF0003, visualizar mensagens no Chat.
Identificador	RF0003
Nome	Visualizar mensagens
Módulo	Chat
Data de criação	19/02/2022	Autor	Tour Geneve
Data da última alteração	19/02/2022	Autor	Tour Geneve
Versão	01	Prioridade	Essencial
Descrição	Permite ao usuário visualizar mensagens através do chat.

Tabela 4 - RF0004, listar todos moradores no Chat.
Identificador	RF0004
Nome	Lista global de moradores
Módulo	Chat
Data de criação	19/02/2022	Autor	Tour Geneve
Data da última alteração	19/02/2022	Autor	Tour Geneve
Versão	01	Prioridade	Essencial
Descrição	Lista ao usuário todos os moradores do condomínio.

Tabela 5 - RF0005, abrir conversa no Chat com base em uma requisição do "Ajude seu Vizinho".
Identificador	RF0005
Nome	Abrir conversa através do “Ajude seu Vizinho”
Módulo	Chat
Data de criação	19/02/2022	Autor	Tour Geneve
Data da última alteração	19/02/2022	Autor	Tour Geneve
Versão	01	Prioridade	Essencial
Descrição	Contactar diretamente em chat privado o morador que publicou uma requisição na funcionalidade Ajude seu Vizinho.

Tabela 6 - RF0006, abrir conversa diretamente com contatos da administração através do Chat.
Identificador	RF0006
Nome	Contactar a administração
Módulo	Chat
Data de criação	19/02/2022	Autor	Tour Geneve
Data da última alteração	19/02/2022	Autor	Tour Geneve
Versão	01	Prioridade	Essencial
Descrição	Enviar mensagem diretamente em chat privado com contatos específicos de administradores e funcionários.

Tabela 7 - RF0007, botão de solicitação de ajuda para vizinhos.
Identificador	RF0007
Nome	Botão Solicitação de Ajuda Para Vizinhos
Módulo	Ajude seu Vizinho
Data de criação	19/02/2022	Autor	Tour Geneve
Data da última alteração	19/02/2022	Autor	Tour Geneve
Versão	01	Prioridade	Essencial
Descrição	Direciona o fluxo do pedido de ajuda para os moradores (vizinhos) do condomínio. Uma solicitação em paralelo é enviada à plataforma GetNinjas.

Tabela 8 - RF0008, botão de solicitação de ajuda para a plataforma GetNinjas.
Identificador	RF0008
Nome	Botão Solicitação de Ajuda Para GetNinjas
Módulo	Ajude seu Vizinho
Data de criação	19/02/2022	Autor	Tour Geneve
Data da última alteração	19/02/2022	Autor	Tour Geneve
Versão	01	Prioridade	Essencial
Descrição	Direciona o fluxo do pedido de ajuda diretamente para a plataforma GetNinjas.

Tabela 9 - RF0009, cadastro de requisição de ajuda.
Identificador	RF0009
Nome	Cadastro de requisição
Módulo	Ajude seu Vizinho
Data de criação	19/02/2022	Autor	Tour Geneve
Data da última alteração	19/02/2022	Autor	Tour Geneve
Versão	01	Prioridade	Essencial
Descrição	Cadastra as requisições (demandas) de ajuda e seus respectivos atributos.

Tabela 10 - RF0010, exclusão de requisição de ajuda.
Identificador	RF0010
Nome	Exclusão de requisição
Módulo	Ajude seu Vizinho
Data de criação	19/02/2022	Autor	Tour Geneve
Data da última alteração	19/02/2022	Autor	Tour Geneve
Versão	01	Prioridade	Essencial
Descrição	Permite que o usuário exclua as requisições (demandas) de ajuda por ele cadastradas.

Tabela 11 - RF0011, edição de requisição de ajuda.
Identificador	RF0011
Nome	Editar requisição
Módulo	Ajude seu Vizinho
Data de criação	19/02/2022	Autor	Tour Geneve
Data da última alteração	19/02/2022	Autor	Tour Geneve
Versão	01	Prioridade	Essencial
Descrição	Permite que o usuário edite as requisições (demandas) de ajuda por ele cadastradas.

Tabela 12 - RF0012, gerenciamento do status da requisição de ajuda.
Identificador	RF0012
Nome	Gerenciar status da requisição
Módulo	Ajude seu Vizinho
Data de criação	19/02/2022	Autor	Tour Geneve
Data da última alteração	19/02/2022	Autor	Tour Geneve
Versão	01	Prioridade	Essencial
Descrição	Permite que o usuário gerencie o status de sua requisição (demanda) se está resolvida ou não.

Tabela 13 - RF0013, listar requisições do usuário.
Identificador	RF0013
Nome	Listar requisições do usuário
Módulo	Ajude seu Vizinho
Data de criação	19/02/2022	Autor	Tour Geneve
Data da última alteração	19/02/2022	Autor	Tour Geneve
Versão	01	Prioridade	Essencial
Descrição	Lista as requisições (demandas) feitas por ele.

Tabela 14 - RF0014, listar requisições com status não resolvido de todos os usuários.
Identificador	RF0014
Nome	Listar requisições de todos usuários
Módulo	Ajude seu Vizinho
Data de criação	19/02/2022	Autor	Tour Geneve
Data da última alteração	19/02/2022	Autor	Tour Geneve
Versão	01	Prioridade	Essencial
Descrição	Lista as requisições (demandas) com status não resolvido de todos os usuários, para que um determinado usuário possa visualizar demandas que ele possa contribuir.

Tabela 15 - RF0015, receber notificações de todos os usuários
Identificador	RF0015
Nome	Receber notificações
Módulo	Notificações
Data de criação	19/02/2022	Autor	Tour Geneve
Data da última alteração	19/02/2022	Autor	Tour Geneve
Versão	01	Prioridade	Essencial
Descrição	O sistema deverá receber notificações de usuários.

Tabela 16 - RF0016, mostrar requisição ao clicar na notificação.
Identificador	RF0016
Nome	Mostrar requisição
Módulo	Notificações
Data de criação	19/02/2022	Autor	Tour Geneve
Data da última alteração	19/02/2022	Autor	Tour Geneve
Versão	01	Prioridade	Essencial
Descrição	O sistema deverá mostrar a requisição referente a notificação.

Tabela 17 - RF0017, excluir a notificação.
Identificador	RF0017
Nome	Excluir notificação 
Módulo	Notificações
Data de criação	19/02/2022	Autor	Tour Geneve
Data da última alteração	19/02/2022	Autor	Tour Geneve
Versão	01	Prioridade	Essencial
Descrição	O sistema deverá excluir a notificação do seu feed dos usuários.

Tabela 18 - RF0018, envia notificações para todos os moradores.
Identificador	RF0018
Nome	Enviar notificações
Módulo	Notificações
Data de criação	20/02/2022	Autor	Tour Geneve
Data da última alteração	20/02/2022	Autor	Tour Geneve
Versão	01	Prioridade	Essencial
Descrição	O sistema deverá enviar notificações para todos os moradores.



4.	Papéis dos membros da equipe Tour Geneve

Alanis Cibele Januário dos Santos: frontend/UX

Jonathan Zils: RFs e backend/arquitetura e banco de dados

Reginaldo de Freitas: RFs e backend/regras de negócio

Lucas Silva de Oliveira: RFs e frontend/UI
Referências de Pesquisa
- https://apcontrole.com.br/
- https://blog.cyrela.com.br/tecnologia-em-condominios/
- https://noknox.com/info/funcionalidades
- https://www.getninjas.com.br/


