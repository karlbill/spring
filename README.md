# Spring
Estudo sobre o framework Spring

## Por que usar Spring?
O Spring é um ecossistema, com diversos braços, cada um responsável por facilicitar determinado módulo de um projeto Java.
O Spring é Open Source e a responsável pelo projeto é a Pivotal.

### Jakarta (JavaEE) x Spring
A plataforma JavaEE passou a se chamar Jakarta EE quando a Eclipse Foundation se tornou responsável pelo projeto.
JPA é uma padronização do Hibernate. Se tornou uma especificação incluída no Jakarta e, após isso, o Hibernate passou a ser uma das implementações da especificação JPA.
Vendor lock-in: ficar preso a um único fornecedor. 
> O Jakarta resolve esse problema com a definição de especificações. Abrindo a possibilidade de implementação para diversos fornecedores.

Vários projetos Spring utilizam especificações o Java EE.
Por exemplo: a classe Model do Spring, contém o método addAttributes que tem a classe HttpServletRequest com seu método addAttributes como implementação de uma especificação JavaEE (Servlets).

## Ecossistema Spring
- Spring Data: facilita a configuração e conexão com bancos de dados, como o Spring Data JPA;
- Spring Security: facilita a configuração de segurança do seu projeto;
- Spring MVC: fornece uma estrutura MVC para seu sistema;
- Spring Framework: contém o Spring MVC, Data Access etc;
- Spring Boot: responsável pela configuração dos demais braços do ecossistema Spring (visão opinativa: convenções de configuração)
> Fornece Starters que agrupam outras dependências. Por exemplo: Spring Web Starter, que é adicionado como uma dependência inicial de um projeto Web.

## Criação de um projeto Spring
[Spring Initializr](start.spring.io)

Maven: 
