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

## Maven
Ferramenta de gerenciamento de dependência e automação de build.

- Estrutura de um projeto Maven (quick-start):

![image](https://user-images.githubusercontent.com/39681960/205499832-81bebdf6-f813-4e0a-a59e-433329f8002d.png)

- Estrutura de um projeto Spring com Maven:

![image](https://user-images.githubusercontent.com/39681960/205500047-19ae26a9-c7f6-41da-9d22-436fed78386d.png)

**pom.xml** (Project Object Model): arquivo que contém as configurações do Maven para o projeto
**mvnw.cmd** e **mvnw**: Maven Wrapper para Windows e Linux, respectivamente. Possibilita a execução do Maven, mesmo que não tenhamos o Maven instalado na máquina.

1. Empacotar o projeto: ``` mvn package ```
> Esse comando irá gerar a pasta target com o arquivo .jar do projeto, que é o projeto empacotado. </br>
> Para rodar o projeto: ``` java -jar demo-0.0.1-SNAPSHOT.jar ```

**Obs: ao rodar o projeto com o comando acima, recebi um erro relacionado ao teste padrão do projeto DemoApplicationTests contextLoads().
Isso porque havia baixado a dependência da especificação JPA mas não havia configurado nenhum banco de dados para o projeto. Então, nesse primeiro momento, comentei essa dependência no pom.xml e rodei novamente o mvn package.**

2. Remover a pasta target: ``` mvn clean ```

## Entendendo o arquivo pom.xml
1. Ao definirmos que o projeto seria do tipo Maven com Spring, o arquivo *pom.xml* contém a tag <parent> que seria uma espécie de herança para o nosso projeto. Ou seja, estamos herdando as configurações de um projeto *spring-boot-starter-parent* da organização *org.springframework.boot*.
> Clicar na tag <parent> com o botão CTRL pressionado fará com que a configuração do pom.xml do projeto pai seja aberto.

![image](https://user-images.githubusercontent.com/39681960/205503241-227b5701-26e7-42b4-81d3-5280511c4661.png)

**Observação: veja que o projeto Spring Boot pai utiliza a versão 8 do Java.**

### Verificando a Hierarquia de Dependências do projeto
Podemos ver como as dependências do projeto foram gerenciadas pelo Maven, analisando sua Hierarquia com o comando: 
- ``` mvn dependency:tree ```

![image](https://user-images.githubusercontent.com/39681960/205503646-6af485ac-a1b6-4c80-86b0-4aeb630ab217.png)

Podemos ver as **dependências resolvidas**, que são, de fato, as dependências do projeto, porque em *dependency:tree* são mostradas subdependências que podem se repetir entre uma dependência e outra. 
> As dependências resolvidas são todas as dependências que o projeto utiliza, sem mostrá-las em uma hierarquia, evitando a repetição.
-  ``` mvn dependency:resolve ```

![image](https://user-images.githubusercontent.com/39681960/205503856-83d61972-3751-483f-afb5-0b17443fad87.png)

Podemos, ainda, ver todas as possíveis dependências que podemos carregar para nosso projeto, a partir da herança do projeto Spring pai.
- ``` mvn help:effective-pom ```

![image](https://user-images.githubusercontent.com/39681960/205503990-cba1976b-6477-43b9-9a9c-147be5311eef.png)

Por fim, as APIs baixadas pelo Maven ficam em um diretório oculto do computador, geralmente: **[usuario]/.m2**

## Spring MVC
O Spring MVC foi adicionado ao projeto a partir da inclusão do Starter Web (spring-boot-starter-web).

### Criação do primeiro Controller
- Criação da camada *controllers*
- Criação do arquivo *TestController.java*
  - Anotação **@Controller**: configura a classe como um **Java Bean**, objetos gerenciados pelo container do Spring.
- Criação do método *test*
  - Anotação **@GetMapping**: configura o endpoint para a *Action* (método) do *Controller* (classe);
  - Anotação **@ResponseBody**: configura a *Action* para aceitar um tipo *String* como retorno
- Utilização da extensão **Rest Client** para realizar as requisições
  - requisição: ``` http://localhost:8080/test ```

```
package br.com.karlbill.demo.controllers;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.ResponseBody;

@Controller
public class TestController {
    
    @GetMapping("/test")
    @ResponseBody
    public String test(){
        return "Test";
    }
}
```

## Injeção de Dependência
O Spring fornece um container específico para Injeção de Dependência e, consequentemente, a Inversão de Controle: o Spring IoC Container.
> Representado pela interface: ApplicationContext.

### Criação de um componente Spring














