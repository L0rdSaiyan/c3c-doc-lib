<!-- Author: Victor Sales -->


<br />
<div align="center">
  <a href="https://github.com/c3csoftware">
    <img src="/imgs/c3clogo.png" alt="Logo" width="80" height="80">
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
          <li><a href="#c3c-callout-config">C3C Callout Config</a></li>
      </ul>
      <ul>
          <li><a href="#c3c-callout-contract">C3C Callout Contract</a></li>
      </ul>
      <li>
          <a href="#criação-da-classe-callout-contract">Criação da classe Callout Contract</a>
      </li>
      <ul>
        <li><a href="#realizando-a-requisição">Realizando a requisição</a></li>
      </ul>
      <ul>
        <li><a href="#obtendo-os-dados-retornados-da-requisição">Obtendo os Dados da Requisição</a></li>
      </ul>
  </ul>
  <li><a href="#classes">Classes e Métodos</a></li>
  <ul>
      <li><a href="#c3c_calloutcontract">C3C_CalloutContract</a></li>
      <ul>
        <li><a href="#sethost">setHost</a></li>
        <li><a href="#seturlpath">setUrlPath</a></li>
        <li><a href="#addurlparam">addUrlParam</a></li>
        <li><a href="#settimeout">setTimeout</a></li>
        <li><a href="#setmethod">setMethod</a></li>
        <li><a href="#setbody">setBody</a></li>
      </ul>
  </ul>
  <li><a href="#objetos">Objetos</a></li>
  <li><a href="#contributing">Contribuidores</a></li>
  <li><a href="#contact">Contato</a></li>
</ol>


## Sobre o Projeto

### Propósito
<span>Essa biblioteca foi desenvolvida visando facilitar as integrações com API's na plataforma Salesforce</span>

## Começando 


### Pré-requsitos

Confirmar com o Luidy dps se a lib só funfa a partir alguma versão específica

### Instalação

1. Acesse a página de deploy da biblioteca 
    <br>
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

![](/imgs/calloutconfig.jpg)

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

<span>Será no metadado C3C Callout Cotnract onde você irá configurar as rotas do Host (API) </span>

![](/imgs/calloutcontract.jpg)

- **1 (Label):** Defina o rótulo de exibição da sua Callout Contract- **OBRIGATÓRIO**
- **2 (C3C Callout Contract Name):** O nome de API de sua Callout Contract - **OBRIGATÓRIO**
- **3 (Protected Component):** Define se o acesso ao metadado dentro de um pacote será limitado.
- **4 (C3C Callout Config):** Callout Config configurada anteriormente
- **5 (Path):** Endpoint o qual o contract fará referência. Também é possível declarar os atributos das url dentro do campo path, como no exemplo:
```
/api/seu_endpoint/atributo={!atributo}
```
- **6 (Contract Class Name):** Classe o qual você deverá criar e ela deve herdar a *C3C_CalloutContract*, pois será ela quem irá montar o contrato com todas as informações presentes nos metadados
- **7 (Global Env. Variables (JSON)):** Definição de variáveis globais em formato JSON, para fácil acesso em seu código Apex
- **8 (Enable Log):** Habilita a criação de Logs com a request e a response dentro do objeto de logs (*C3C_Log*)
- **9 (Method):** Verbo HTTP utilizados para indicar a ação que deve ser realizada no chamado para o endpoint
- **10 (Timeout):** O tempo o qual a classe contrato deverá esperar para receber algum retorno da API
- **11 (Success Codes):** Status que indicaram sucesso ao se comunicar com a API 
- **12 (Is it an authorization service?):**
- **13 (Timeframe for execution (Hours)):**
- **14 (Token Extraction Class Name):**

#### Criação da classe Callout Contract

Como mencionado no tópico anterior, você precisará de uma classe de Callout Contract para que sua requisição possa funcionar. 

Você deverá herdar a classe **C3C_CalloutContract** em sua classe contrato e sobrescrever o método **buildContract**. No final, sua classe contrato deverá seguir essa estrutura:

```apex
public class YourContract extends C3C_CalloutContract{

    public override void buildContract(Object request)
    {
        
    }
    
}
```
### Realizando a Requisição
Após a criação da classe de contrato, realizar a requisição torna-se bastante simples.  

No developer console, execute:
```apex
C3C_RestService.service.sendRequest(QuemChamou, seuMetadadoDeContrato);
```
**QuemChamou**: *this* ou sua *classe callout* (String)
<br>
**seuMetadadoDeContrato**: o metadado de contrato definido por você anteriormente

Requisição dentro de uma classe:
```apex
public class UserCallout {
    
    public void fetchAllUsers()
    {
        C3C_RestService.service.sendRequest(this, 'getAllEmployees');
       
    }
    
}
```

### Obtendo os dados retornados da requisição:
Como o método **sendRequest** retorna um objeto da classe **C3C_CalloutResponseDTO**, podemos obter tanto a request quanto a response da requisição.

```apex
 C3C_CalloutResponseDTO dataTransferObject = C3C_RestService.service.sendRequest(QuemChamou, seuMetadadoDeContrato);

```

Obtendo o body da resposta:

```apex
 C3C_CalloutResponseDTO dataTransferObject = C3C_RestService.service.sendRequest(QuemChamou, seuMetadadoDeContrato);
System.debug(dataTransferObject.response.getBody());
```

## Classes

### C3C_CalloutContract

### Métodos

#### buildContract

 Ele deve ser sobrescrito obrigatoriamente por qualquer classe que estenda a C3C_CalloutContract. O objetivo principal deste método é montar o contrato com base nas configurações e dados recebidos. Aqui está uma explicação detalhada do funcionamento:

```apex
public class YourContract extends C3C_CalloutContract{

    public override void buildContract(Object request)
    {
       
    }
    
}
```

O parâmetro request do tipo Object é utilizado para capturar os dados que estão sendo passados para o contrato. Estes dados representam toda a informação enviada na requisição, como parâmetros, corpo da requisição, e cabeçalhos, dependendo da necessidade da chamada.

O método buildContract serve para ajustar as configurações da chamada de API de forma dinâmica, conforme os dados que foram passados pelo parâmetro request. 

#### setHost

<span>O método setHost irá sobrescrever, em sua classe, a informação de Host no seu metadado callout contract</span>

```apex
public class YourContract extends C3C_CalloutContract{

    public override void buildContract(Object request)
    {
        this.setHost('seuNovoHost'); // https://seuNovoHost.com
    }
    
}
```

#### setUrlPath

<span> O método setUrlPath irá sobrescrever, em sua classe, a informação de Url Path da requisição no seu metadado Callout Contract</span>

```apex
public class YourContract extends C3C_CalloutContract{
    public override void buildContract(Object request)
    {
        this.setUrlPath('seuNovoUrlPath'); // https://seuNovoHost.com/seuNovoUrlPath
    }
}
```
#### addUrlParam irá adicionar, em sua url, parâmetros.

```apex
public class YourContract extends C3C_CalloutContract{
    public override void buildContract(Object request)
    {
        this.addUrlParam('parametro', 'valor'); // parametro: valor
    }
}
```
Com esse método, você não precisa declarar uma variável em seu path no metadado de contrato.

#### setTimeout

Com esse método, você irá sobrescrever o tempo de espera pela resposta da API presente em seu metadado de contrato.

```apex
public class YourContract extends C3C_CalloutContract{
    public override void buildContract(Object request)
    {
        //exemplo o qual irá mudar o timeout para 120000
        this.setTimeout(120000);
    }
}
```

#### setMethod

Esse método irá sobrescrever o verbo HTTP definido no metadado de contrato

```apex
public class YourContract extends C3C_CalloutContract{
    public override void buildContract(Object request)
    {
        //exemplo o qual irá mudar o método para POST
        this.setMethod('POST');
    }
}
```

#### setBody

Com esse método, você consegue enviar o body para uma requisição.

```apex
public class YourContract extends C3C_CalloutContract{
    public override void buildContract(Object request)
    {
        //Você só precisará fazer o casting para o tipo do body que você deseja.
        this.setBody((String) request);
    }
}
```
Exemplo de uso:
```apex
public UserViewModel createUser(UserViewModel newUser)
    {
		
        String userJSON = JSON.serialize(newUser);
        C3C_CalloutResponseDTO response = C3C_RestService.service.sendRequest(this, 'funcionarioCreation', userJSON);
        UserViewModel createdUser = new UserViewModel();
        if(response.isResponseSuccess)
        {
		createdUser = (UserViewModel) JSON.deserialize(response.response.getBody(), UserViewModel.class);
        }
        
        return createdUser;
        
        
    }
```

#### addHeaderLine

Com esse método, você consegue enviar o header para uma requisição.

```apex
public class YourContract extends C3C_CalloutContract{
    public override void buildContract(Object request)
    {
	this.addHeaderLine(String key, String value); // key: value
    }
}
```

#### setSuccessCodes

Com esse método, você consegue sobrescrever o código de sucesso da requisição no seu metadado Callout Contract.

```apex
public class YourContract extends C3C_CalloutContract{
    public override void buildContract(Object request)
    {
	this.setSuccessCodes(String successCodes);
    }
}
```

#### addEndpointKeyValue

Com esse método, você consegue adicionar algum valor dinamicamente no path da requisição informado pelo seu metadado Callout Contract.

```apex
public class YourContract extends C3C_CalloutContract{
    public override void buildContract(Object request)
    {
	// path: /api/exemplo/{!example}
	this.keysEndpoint.put(key, value); // 'example' : (String) request;
    }
}
```
