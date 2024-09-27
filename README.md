
<br />
<div align="center">
  <a href="https://github.com/github_username/repo_name">
    <img src="https://media.discordapp.net/attachments/472081051120828416/1288998376955973642/c3c-software-logo.png?ex=66f738c9&is=66f5e749&hm=0d07768e0003686e053eb36ef24e4c0c7867965bd4ab47ab4638ce35dac7ef28&=&format=webp&quality=lossless" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">C3C Software Callout LIB</h3>

  <p align="center">
    Biblioteca para chamadas à API's
    <br />
    <br />
    <br />
    ·
    <a href="https://github.com/c3csoftware/LIB_C3C_CALLOUT/issues/new?labels=bug&template=bug-report---.md">Report  de Bugs</a>
    ·
    <a href="https://github.com/c3csoftware/LIB_C3C_CALLOUT/issues/new?labels=enhancement&template=feature-request---.md">Sugerir nova Feature</a>
  </p>
</div>


  
<!-- TABLE OF CONTENTS -->
<details>
  <summary>Conteúdo</summary>
  <ol>
    <li>
      <a href="#sobre-o-projeto">Sobre o Projeto</a>
      <ul>
        <li><a href="#propósito">Propósito</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Começando</a>
      <ul>
        <li><a href="#instalação">Instalação</a></li>
      </ul>
    </li>
    <li><a href="#uso">Uso</a></li>
    <ul>
        <li><a href="#metadados">Metadados</a></li>
        <ul>
            <li><a href="#calloutconfig">C3C Callout Config</a></li>
        </ul>
        <ul>
            <li><a href="#calloutcontract">C3C Callout Contract</a></li>
        </ul>
    </ul>
    <li><a href="#contributing">Contribuidores</a></li>
    <li><a href="#contact">Contato</a></li>
  </ol>
</details>

## Sobre o Projeto

### Propósito
<span>Essa biblioteca foi desenvolvida visando facilitar as integrações com API's na plataforma Salesforce</span>

## Começando 


### Pré-requsitos

Confirmar com o Luidy dps se a lib só funfa a partir alguma versão específica

### Instalação

1. Acesse a página de deploy da biblioteca 
    <a href="https://githubsfdeploy.herokuapp.com?owner=c3csoftware&repo=LIB_C3C_CALLOUT">
  <img alt="Deploy to Salesforce"
       src="https://raw.githubusercontent.com/afawcett/githubsfdeploy/master/deploy.png">
</a>

2. Faça login (canto superior direito) na organização onde deseje implantar a biblioteca
3.  Clique em "Deploy"

## Uso

### Metadados
<span>Os metadados de configuração que são implantados juntos da biblioteca foram pensados para facilitarem a configuração até a chamada da requisição no Apex</span>

#### C3C Callout Config
   <span>Trata-se da configuração **macro** do sistema externo</span>

![](https://media.discordapp.net/attachments/472081051120828416/1289012142246465617/image.png?ex=66f7459b&is=66f5f41b&hm=7272f6c2a9ff148b17ae291ec24906fd823916e9fa2e636dce90b44c74f706df&=&format=webp&quality=lossless)

- **1 (Label):** Defina o rótulo de exibição da sua Callout Config - **OBRIGATÓRIO**
- **2 (C3C Callout Config Name):** O nome de API de sua Callout Config - **OBRIGATÓRIO**
- **3 (Host):** Defina a URL base de sua API (Lembre-se autorizar o site remoto nas configurações) -**OBRIGATÓRIO**
- **4 (Global Env. Variables (JSON)):** Definição de variáveis globais em formato JSON, para fácil acesso em seu código Apex
- **5 (Protected Component):** Define se o acesso ao metadado dentro de um pacote será limitado.
- **6 (Segredo do Cliente):** chave secreta utilizada em autenticações OAuth 2.0 e em outros tipos de autenticação de APIs. 
- **7 (Código de Autorização Fixo):** Se a API possuir um código de autorização fixo, cole-o no campo.
- **8 (Nome do código de autorização):** Se a API possuir um código de autorização que não é fixo, cole-o no campo.
- **9 (Enable Log):** Habilita a criação de Logs com a request e a response dentro do objeto de logs (*C3C_Log*)
- **10 (Id do cliente):** Um identificador público único que representa o aplicativo
- **11(Authorization Code Type):** métodos de autenticação e autorização (Bearer e Basic) em APIs e sistemas de autenticação, especialmente em protocolos como OAuth 2.0

#### C3C Callout Contract

<p align="right">(<a href="#readme-top">back to top</a>)</p>
