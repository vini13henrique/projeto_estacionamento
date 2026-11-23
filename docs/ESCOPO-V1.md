# Escopo do Projeto — V1

## 1. Visão geral

O projeto consiste no desenvolvimento de um sistema web para o gerenciamento de estacionamentos, com o objetivo de organizar e administrar as operações diárias.

O sistema será utilizado por administradores e clientes cadastrados.

Os administradores poderão gerenciar vagas, registrar entradas e saídas de veículos, consultar dados dos clientes e visualizar o histórico de estacionamentos.

Os clientes poderão criar uma conta, realizar login, consultar seus próprios dados e visualizar seu histórico de estacionamentos.

## 2. Objetivo da V1

A primeira versão tem como objetivo disponibilizar as funcionalidades essenciais para o gerenciamento de um estacionamento, incluindo:

- Cadastro e autenticação de usuários.
- Cadastro de clientes com CPF.
- Gerenciamento e controle de vagas.
- Registro de entrada (check-in) e saída (check-out) de veículos.
- Cálculo automático dos valores de estacionamento e descontos de fidelidade.
- Geração de recibos para identificação dos estacionamentos.
- Consulta do histórico de estacionamentos.
- Geração de relatórios em PDF para os clientes.

## 3. Tecnologias utilizadas

### 3.1 Backend

| Tecnologia | Finalidade |
|---|---|
| Java 21 | Linguagem de programação utilizada no backend. |
| Spring Boot | Framework para desenvolvimento da API REST. |
| Spring Security | Autenticação e autorização dos usuários. |
| JWT | Autenticação baseada em tokens. |

### 3.2 Banco de dados

| Tecnologia | Finalidade |
|---|---|
| PostgreSQL | Armazenamento e gerenciamento dos dados. |
| Flyway | Controle de versões e evolução da estrutura do banco de dados. |

### 3.3 Frontend

| Tecnologia | Finalidade |
|---|---|
| HTML5 | Estrutura das páginas web. |
| CSS3 | Estilização e responsividade da interface. |
| JavaScript | Interatividade e comunicação com a API REST. |

### 3.4 Ferramentas de desenvolvimento e testes

| Tecnologia | Finalidade |
|---|---|
| Maven | Gerenciamento de dependências e construção do projeto. |
| Git | Controle de versões do código. |
| GitHub | Hospedagem do repositório e gerenciamento de Pull Requests. |
| IntelliJ IDEA | Ambiente de desenvolvimento e depuração da aplicação. |
| JUnit | Criação e execução de testes no backend. |
| Mockito | Simulação de dependências nos testes do backend. |

A ferramenta específica para testes unitários do frontend será definida durante a implementação.

## 4. Requisitos funcionais

Os requisitos funcionais descrevem as funcionalidades e operações que o sistema deverá oferecer aos usuários.

### 4.1 Gerenciamento de usuários

- **RF-001 — Cadastro de usuários:** o sistema deverá permitir o cadastro público de usuários utilizando e-mail e senha, atribuindo automaticamente o perfil de cliente. O e-mail deverá ser único.

- **RF-002 — Autenticação:** o sistema deverá permitir a autenticação por e-mail e senha, utilizando JSON Web Token (JWT).

- **RF-003 — Consulta de usuários:** o administrador poderá consultar qualquer usuário pelo identificador. Clientes poderão consultar somente os próprios dados.

- **RF-004 — Alteração de senha:** usuários autenticados poderão alterar suas próprias senhas.

- **RF-005 — Listagem de usuários:** o administrador poderá consultar a lista de todos os usuários cadastrados.

### 4.2 Gerenciamento de clientes

- **RF-006 — Cadastro de clientes:** o sistema deverá permitir que um usuário com perfil de cliente realize seu cadastro, informando nome completo e CPF único.

- **RF-007 — Vinculação de usuários:** cada cadastro de cliente deverá estar vinculado a um único usuário, não sendo permitido mais de um cadastro de cliente para o mesmo usuário.

- **RF-008 — Consulta de clientes:** o administrador poderá consultar clientes pelo identificador e listar todos os clientes cadastrados.

- **RF-009 — Consulta dos próprios dados:** o cliente autenticado poderá consultar suas informações cadastrais.

### 4.3 Gerenciamento de vagas

- **RF-010 — Cadastro de vagas:** o administrador poderá cadastrar vagas, cada uma com um código único, independente do identificador do banco de dados.

- **RF-011 — Controle de ocupação:** o sistema deverá controlar o status das vagas, identificando-as como livres ou ocupadas.

- **RF-012 — Consulta de vagas:** o administrador poderá localizar vagas pelo código e consultar vagas disponíveis. Em caso de tentativa de ocupação de uma vaga já utilizada, o sistema deverá bloquear a operação e sugerir outra vaga livre.

### 4.4 Gerenciamento de estacionamentos

- **RF-013 — Check-in:** o administrador poderá registrar a entrada de veículos pertencentes a clientes cadastrados, informando o CPF do cliente, placa, marca, modelo, cor e vaga utilizada. O sistema deverá registrar a data e hora da entrada e gerar um número de recibo único.

- **RF-014 — Check-out:** o administrador poderá registrar a saída de um veículo mediante a apresentação do número do recibo, registrando a data e hora da saída, o valor da permanência e o desconto aplicado, quando houver.

- **RF-015 — Atualização das vagas:** o sistema deverá atualizar automaticamente a ocupação da vaga após o check-in e liberá-la após a conclusão do check-out.

- **RF-016 — Consulta por recibo:** administradores poderão consultar registros de estacionamento pelo número do recibo. Clientes poderão consultar somente os registros vinculados ao próprio cadastro.

- **RF-017 — Histórico de estacionamentos:** o administrador poderá consultar os estacionamentos pelo CPF do cliente. Cada cliente poderá consultar somente o próprio histórico.

### 4.5 Cobrança e fidelidade

- **RF-018 — Cálculo de cobrança:** o sistema deverá calcular automaticamente o valor da permanência de acordo com o tempo estacionado e a tabela de preços estabelecida.

- **RF-019 — Desconto de fidelidade:** o sistema deverá controlar os estacionamentos concluídos por cliente e aplicar automaticamente o desconto de 30% quando o cliente atingir as condições estabelecidas pelas regras de negócio.

### 4.6 Relatórios

- **RF-020 — Relatório em PDF:** o cliente autenticado poderá gerar um relatório em PDF contendo seu histórico de estacionamentos.

### 4.7 Interface web

- **RF-021 — Interface do sistema:** o sistema deverá disponibilizar uma interface web para autenticação e utilização das funcionalidades permitidas a cada perfil, respeitando as permissões estabelecidas no backend.

## 5. Requisitos não funcionais

Os requisitos não funcionais estabelecem características de segurança, qualidade, manutenção e confiabilidade do sistema.

### 5.1 Segurança

- **RNF-001:** a API deverá utilizar Spring Security e autenticação baseada em JWT.
- **RNF-002:** as senhas deverão ser armazenadas utilizando um algoritmo seguro de hash, nunca em texto puro.
- **RNF-003:** o backend deverá validar os dados recebidos e verificar as permissões de acesso.
- **RNF-004:** o banco de dados deverá utilizar restrições de integridade e mecanismos adequados de proteção contra operações inconsistentes.
- **RNF-005:** senhas, tokens e outras informações sensíveis não poderão ser expostos em logs ou armazenados no repositório Git.

### 5.2 Banco de dados

- **RNF-006:** o sistema deverá utilizar PostgreSQL como banco de dados relacional.
- **RNF-007:** as alterações na estrutura do banco deverão ser versionadas utilizando Flyway.
- **RNF-008:** deverão ser utilizadas chaves primárias, estrangeiras e restrições de integridade conforme a modelagem.
- **RNF-009:** operações que modificam dados relacionados deverão utilizar transações quando necessário, garantindo sua consistência.

### 5.3 Auditoria e observabilidade

- **RNF-010:** os registros deverão possuir informações de criação e última alteração, incluindo data, hora e usuário responsável, conforme aplicável.
- **RNF-011:** o sistema deverá registrar logs relevantes para acompanhamento de operações e identificação de erros.
- **RNF-012:** a aplicação deverá possuir tratamento global de exceções, retornando respostas padronizadas e sem expor detalhes internos.
- **RNF-013:** a API deverá utilizar o fuso horário `America/Sao_Paulo` e as configurações regionais `pt-BR`, conforme definido para o projeto.

### 5.4 Qualidade e testes

- **RNF-014:** o backend deverá possuir testes unitários utilizando JUnit e Mockito.
- **RNF-015:** o frontend deverá possuir testes unitários para suas principais funções e comportamentos.
- **RNF-016:** deverão ser realizados testes de integração envolvendo API e banco de dados, incluindo os fluxos principais.
- **RNF-017:** a cobertura de testes unitários terá como referência de 70% a 80% do código relevante, priorizando testes úteis e não apenas a porcentagem.
- **RNF-018:** o desenvolvimento deverá seguir princípios básicos de Clean Code, utilizando nomes claros, responsabilidades bem definidas e evitando complexidade desnecessária.

### 5.5 Interface e documentação

- **RNF-019:** a interface web deverá ser responsiva, permitindo sua utilização em computadores e dispositivos móveis.
- **RNF-020:** a interface deverá apresentar mensagens adequadas para operações bem-sucedidas, erros e carregamentos.
- **RNF-021:** a API REST deverá possuir documentação de seus endpoints, parâmetros e respostas.
- **RNF-022:** o projeto deverá possuir documentação de configuração, execução e testes.

### 5.6 Versionamento

- **RNF-023:** o código-fonte deverá ser versionado utilizando Git e hospedado no GitHub.
- **RNF-024:** o desenvolvimento seguirá o fluxo de branches `main`, `develop` e `feature/*`, utilizando branches de release e hotfix quando necessário.
- **RNF-025:** as alterações deverão ser organizadas em commits pequenos e descritivos, escritos em português.
- **RNF-026:** a integração das funcionalidades deverá ocorrer após revisão e execução dos testes aplicáveis.

## 6. Regras de negócio

As regras de negócio estabelecem as condições, restrições e comportamentos que deverão ser respeitados pelo sistema.

### RN-001 — Cadastro de usuários e administradores

- O cadastro público deverá criar exclusivamente usuários com perfil `CLIENTE`.
- O e-mail utilizado no cadastro deverá ser único.
- O administrador inicial será criado por um procedimento técnico controlado.
- Não será permitido atribuir o perfil `ADMIN` por meio do cadastro público.
- Não haverá funcionalidade de cadastro de novos administradores pela interface na V1.

### RN-002 — Política de senhas

- As senhas deverão possuir no mínimo 8 caracteres.
- As senhas deverão ser armazenadas de forma segura, utilizando hash.
- Somente o próprio usuário autenticado poderá alterar sua senha.
- Senhas inválidas deverão ser rejeitadas pelo backend.

### RN-003 — Controle de ocupação das vagas

- Cada vaga deverá possuir um código único e um status `LIVRE` ou `OCUPADA`.
- Não será permitido registrar a entrada de um veículo em uma vaga ocupada.
- Quando a vaga solicitada estiver ocupada, o sistema deverá bloquear a operação e sugerir outra vaga livre, quando disponível.
- O administrador deverá confirmar a utilização da vaga sugerida.
- Caso não existam vagas disponíveis, o sistema deverá informar a indisponibilidade e impedir o check-in.
- A mesma vaga poderá ser utilizada por diferentes veículos em momentos distintos, mas nunca simultaneamente.

### RN-004 — Check-out duplicado

- Não será permitido realizar o check-out de um estacionamento já finalizado.
- O sistema deverá informar que a saída já foi registrada.
- A data de saída, o valor cobrado e o desconto aplicado deverão permanecer inalterados.
- A tentativa duplicada não poderá gerar nova cobrança nem modificar a ocupação de outras vagas.

### RN-005 — Desconto de fidelidade

- Somente estacionamentos com entrada e saída concluídas serão considerados na contagem de fidelidade.
- Após cada grupo de 10 estacionamentos concluídos, o próximo estacionamento concluído receberá 30% de desconto.
- O desconto será aplicado no 11º, 21º, 31º estacionamento concluído e assim sucessivamente.
- Os estacionamentos que receberam desconto também serão considerados na contagem.
- O desconto será calculado automaticamente durante o check-out.
- Cada estacionamento poderá receber o desconto apenas uma vez.

### RN-006 — Cálculo da cobrança

O valor do estacionamento será calculado conforme o tempo de permanência.

| Tempo de permanência | Valor |
|---|---|
| De 0 a 15 minutos | R$ 5,00 |
| Acima de 15 até 60 minutos | R$ 9,25 |
| Acima de 60 minutos | R$ 9,25 + R$ 1,75 por faixa adicional de 15 minutos iniciada |

Condições adicionais:

- O valor mínimo da permanência será de R$ 5,00, inclusive para saída imediata.
- Cada faixa adicional iniciada após os primeiros 60 minutos será cobrada integralmente.
- Não será permitido calcular uma permanência com data de saída anterior à data de entrada.
- O desconto de fidelidade, quando aplicável, será calculado sobre o valor da permanência.
- O valor final deverá ser arredondado para duas casas decimais, utilizando arredondamento comercial.

### RN-007 — Controle de veículos estacionados

- Uma placa não poderá possuir mais de um estacionamento ativo simultaneamente.
- Caso o veículo já esteja estacionado, uma nova tentativa de check-in deverá ser bloqueada.
- Após o check-out, o mesmo veículo poderá realizar uma nova entrada.
- O backend e o banco de dados deverão garantir a consistência dessa restrição, inclusive em requisições simultâneas.

### RN-008 — Cadastro obrigatório de clientes

- Somente clientes cadastrados poderão utilizar o estacionamento.
- O cliente deverá possuir CPF único e estar vinculado a um usuário.
- Um usuário poderá estar vinculado a apenas um cadastro de cliente.
- Para realizar o check-in, será necessário informar o CPF de um cliente cadastrado.
- Caso o CPF não corresponda a um cliente cadastrado, o sistema deverá rejeitar a operação.

### RN-009 — Recibos de estacionamento

- Cada check-in deverá gerar um número de recibo único.
- O recibo deverá identificar o registro de estacionamento.
- O número do recibo deverá ser utilizado para realizar o check-out.
- Administradores poderão consultar estacionamentos por recibo.
- Clientes poderão consultar somente os recibos vinculados ao próprio cadastro.

### RN-010 — Permissões de acesso

- Administradores poderão gerenciar vagas, registrar check-ins e check-outs e consultar os dados autorizados pela demanda.
- Clientes poderão consultar seus próprios dados, histórico e relatórios.
- As operações restritas deverão exigir autenticação.
- O backend deverá verificar as permissões independentemente das validações realizadas no frontend.

## 7. Critérios de conclusão da V1

A V1 será considerada concluída quando os requisitos definidos estiverem implementados e validados.

### 7.1 Funcionalidades

- [ ] Cadastro e autenticação de usuários funcionando.
- [ ] Controle de permissões de administradores e clientes implementado.
- [ ] Cadastro e consulta de clientes funcionando.
- [ ] Gerenciamento de vagas implementado.
- [ ] Check-in e check-out funcionando conforme as regras de negócio.
- [ ] Geração de recibos únicos implementada.
- [ ] Cálculo de cobranças e descontos validado.
- [ ] Consulta de histórico funcionando.
- [ ] Geração de relatórios em PDF implementada.
- [ ] Frontend responsivo integrado à API.

### 7.2 Segurança e banco de dados

- [ ] Autenticação JWT e autorização implementadas.
- [ ] Senhas armazenadas de maneira segura.
- [ ] Validações e restrições de integridade aplicadas.
- [ ] Migrations do Flyway funcionando.
- [ ] Operações críticas protegidas por transações e mecanismos de consistência.

### 7.3 Testes e qualidade

- [ ] Testes unitários do backend implementados com JUnit e Mockito.
- [ ] Testes unitários do frontend implementados.
- [ ] Testes de integração dos principais fluxos executados.
- [ ] Cobertura de testes avaliada, priorizando regras críticas.
- [ ] Tratamento global de exceções implementado.
- [ ] Logs básicos e auditoria funcionando.
- [ ] Fluxos críticos depurados e validados.

### 7.4 Documentação e entrega

- [ ] API REST documentada.
- [ ] README com instruções de instalação, execução e testes.
- [ ] Código versionado no GitHub, seguindo o fluxo definido.
- [ ] Versão final revisada e identificada por uma tag Git.
- [ ] Deploy realizado e fluxos principais testados no ambiente publicado, ou limitações de hospedagem documentadas caso impeçam a publicação.

A conclusão da V1 encerra o escopo desta versão. A reconstrução do frontend com React será tratada posteriormente, como uma nova etapa de aprendizado.