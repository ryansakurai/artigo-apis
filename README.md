# APIs: a Diplomacia no Mundo da Tecnologia

## Introdução

No universo da tecnologia, alguns conceitos têm papeis essenciais nos bastidores, mas são quase invisíveis aos olhos do usuário final. Um deles é a API (*Application Programming Interface*), ou Interface de Programação de Aplicações. Assim como diplomatas facilitam a comunicação entre nações, as APIs atuam como intermediárias silenciosas, garantindo que softwares distintos possam "conversar", trocar informações e trabalhar em harmonia.

Para entender as APIs, é preciso primeiro compreender o que é uma interface. Interfaces operam com base em dois pilares: abstração e encapsulamento. A abstração esconde complexidades, permitindo que utilizemos algo sem precisar entender seu funcionamento interno, assim como você não precia entender o funcionamento interno de um celular para utilizá-lo. Já o encapsulamento protege os detalhes técnicos, expondo apenas o que é necessário para a interação.

Um controle remoto de TV, por exemplo, é uma interface física: você aperta botões para mudar de canal sem precisar entender como ele funciona por dentro. Da mesma forma, um aplicativo de banco, que é uma interface gráfica, ou GUI (*Graphical User Interface*) simplifica operações complexas: com alguns cliques, você transfere dinheiro sem ver os sistemas de segurança ou bancos de dados por trás. As APIs funcionam da mesma maneira, porém, ao contrário das interfaces citadas, que são feitas para usuários finais, as APIs são feitas para serem usadas por programas

No Spotify, por exemplo, quando um desenvolvedor cria o botão de "play" no aplicativo, ele utiliza uma API de uma biblioteca de interfaces gráficas para mostrar o botão visualmente. A essa interface pré-construída, ele adiciona a lógica específica da aplicação. Quando o usuário clica no botão, a aplicação aciona a API do servidor do Spotify para obter os dados da música (arquivo de áudio, metadados, etc.). Em seguida, para reproduzir o áudio, o aplicativo utiliza a API do sistema operacional, como o Android, que controla o hardware do dispositivo, garantindo que o som saia pelo fone do usuário. Paralelamente, se a letra da música aparece na tela, isso ocorre porque o Spotify integra uma API externa, a do Musixmatch, que fornece as letras sincronizadas em tempo real. Cada etapa desse processo depende de APIs distintas e de diferentes tipos, todas trabalhando em conjunto para que a aplicação funcione.

## Tipos de API

Quando falamos de APIs, normalmente nos referimos a APIs Web, que permitem a comunicação entre aplicações via internet. No entanto, as APIs estão presentes em qualquer contexto de desenvolvimento e em qualquer tipo de software, atuando como pontes entre componentes de um sistema. Abaixo, exploro alguns dos principais tipos:

### APIs de Sistema Operacional

Essas APIs permitem que aplicativos interajam com recursos do sistema operacional, como *hardware*, serviços de arquivo ou redes. No exemplo anterior usando o Spotify, o aplicativo utiliza a API do Android ou iOS para acessar o controle de áudio do dispositivo. A existência dessas APIs é a razão pela qual muitos programas podem ser independentes de sistema operacional: elas abstraem detalhes de implementação específicos de cada SO, permitindo que desenvolvedores criem aplicações compatíveis com múltiplas plataformas.

### APIs de Linguagens de Programação

Linguagens de programação oferecem APIs nativas para simplificar operações rotineiras na linguagem. Um exemplo é a Collections API do Java, que fornece estruturas de dados prontas, como listas (`ArrayList`, `LinkedList`), conjuntos (`HashSet`, `TreeSet`) e mapas (`HashMap`). Essas estruturas são acessadas por meio de interfaces padronizadas, permitindo que desenvolvedores manipulem dados sem se preocupar com detalhes de implementação. Por exemplo, ao usar a interface `List`, abstrai-se como os elementos são armazenados internamente. Isso garante flexibilidade: é possível alternar entre `ArrayList` e `LinkedList` sem alterar a lógica principal do programa.

### APIs de Bibliotecas e Frameworks

Bibliotecas e frameworks também disponibilizam APIs para simplificar problemas recorrentes. Um exemplo é a biblioteca React, que oferece funções e componentes pré-definidos (como `Fragment` e hooks) para construção de interfaces de usuário. No caso do Spotify, o botão de "play" pode ser criado usando a API de uma biblioteca gráfica, que encapsula a renderização visual e eventos de clique.

### APIs Remotas

São APIs acessíveis via rede, geralmente utilizando protocolos como HTTP. O Spotify, por exemplo, usa a API do Musixmatch para exibir letras de músicas em tempo real. As API web previamente citadas são um tipo de API remota e serão exploradas com mais profundidade a seguir.

## APIs Web

As APIs Web são interfaces que permitem a comunicação entre aplicações através da internet, utilizando protocolos como HTTP. Sua popularidade cresceu com a computação em nuvem, microsserviços e aplicações multiplataforma, que exigem interoperabilidade e escalabilidade. Endpoints são elementos fundamentais nesse contexto: trata-se de URIs (*Uniform Resource Identifier*), ou Identificador Uniforme de Recurso, que uma API expõe para acesso a recursos ou funcionalidades. Por exemplo, um endpoint como /musicas pode ser acessado para retornar uma lista de músicas. Para garantir a seguraça no uso dessas APIs, são frequentemente utilizados tokens de autenticação para controle de acesso e para previnir mal uso das APIs.

Três motivos principais impulsionam sua adoção: delegação de processamento, que alivia a carga computacional nos dispositivos finais ao transferir tarefas complexas para o servidor; economia de memória, já que dados podem ser acessados sob demanda, reduzindo a necessidade de armazenamento local; e facilidade de integração, graças à padronização que simplifica a conexão entre sistemas heterogêneos.

Dentre as tecnologias relacionadas, abordaremos SOAP, REST, GraphQL, WebSocket e Webhooks. Embora nem todas se enquadrem estritamente na definição técnica de APIs Web, todas estão interligadas no ecossistema moderno. Além disso, há variações no nível de abstração dos conceitos e em suas classificações.

### SOAP

O SOAP (Simple Object Access Protocol), ou Protocolo Simples de Acesso a Objetos, é um protocolo padronizado para troca de dados estruturados entre aplicações. Projetado para ser independente de plataforma e linguagem, ele usa XML para formatar mensagens e é majoritariamente usado através de HTTP, apesar de algumas aplicações mais antigas utilizarem outros protocolos. A seguir está um exemplo de troca de mensagens SOAP:

```xml
<?xml version="1.0" encoding="utf-8"?>
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Body>
    <GetMusicaInfos xmlns="http://api.com/soap">
      <musicaId>1234</musicaId>
    </GetMusicaInfos>
  </soap:Body>
</soap:Envelope>
```

```xml
<?xml version="1.0" encoding="utf-8"?>
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Body>
    <m:GetMusicaInfosResposta xmlns:m="http://api.com/soap">
      <m:Musica>
        <m:Titulo>Purity Weeps</m:Titulo>
        <m:Artista>Invent Animate</m:Artista>
        <m:Lancamento>Heavener</m:Lancamento>
        <m:Duracao>04:08</m:Duracao>
        <m:Generos>
          <m:Genero>Metalcore</m:Genero>
          <m:Genero>Metal Progressivo</m:Genero>
        </m:Generos>
      </m:Musica>
    </m:GetMusicaInfosResposta>
  </soap:Body>
</soap:Envelope>
```

Ele é baseado em serviços e sua estrutura rígida é definida por um contrato formal chamado WSDL (Web Services Description Language), ou Linguagem de Descrição de Serviços Web, que descreve as operações disponíveis e os formatos de entrada/saída da API. Por exemplo, um serviço bancário pode usar WSDL para especificar como uma transferência deve ser solicitada, incluindo campos como valor, conta destino e autenticação.

O SOAP se destaca em ambientes que exigem alta segurança e confiabilidade, como sistemas financeiros ou governamentais. Ele suporta padrões avançados de criptografia e transações ACID (Atomicidade, Consistência, Isolamento, Durabilidade), essenciais para operações críticas. Além disso, é utilizado em sistemas legados, onde a estabilidade e a adesão a regras bem-definidas são prioritárias.

Apesar de sua robustez, o SOAP é criticado por sua verbosidade (devido ao XML) e complexidade, o que faz com que não seja tão amplamente usado atualmente. No entanto, em cenários onde a precisão e a segurança superam a necessidade de agilidade, ele permanece uma escolha relevante.

### REST

REST (*Representational State Transfer*), ou Transferência de Estado Representacional, é o tipo de API mais utilizado na atualidade, destacando-se pela flexibilidade e leveza em comparação a protocolos mais rígidos como o SOAP. Enquanto o SOAP depende de especificações formais, o REST segue princípios flexíveis, priorizando simplicidade e eficiência na comunicação entre sistemas.

Sua arquitetura é centrada em recursos e coleções, entidades acessíveis por meio de URLs (tipos de URI). Por exemplo, ao acessar um endpoint como `https://api.com/musicas`, o cliente pode criar um novo recurso na coleção de músicas e, ao acessar `https://api.com/musicas/1234`, o cliente pode solicitar dados de uma música específica identificada pelo número 1234. Essas entidades são geralmente representadas em JSON (*JavaScript Object Notation*), ou Notação de Objeto Javascript, um formato leve, legível e fácil de processar.

A comunicação em REST utiliza métodos HTTP para definir ações sobre os recursos, seguindo uma lógica intuitiva: `GET` recupera recursos, `POST` os cria, `PUT` os atualiza por completo, `PATCH` os modifica parcialmente e `DELETE` os remove. Para especificar como e o quê deve ser acessado, os URLs podem incluir parâmetros de caminho (ex.: /musicas/123, onde 123 especifica o ID da música) para identificar recursos específicos e parâmetros de query (ex.: /musicas?genero=metal), usados para filtrar, ordenar ou paginar resultados. Isso permite requisições precisas, como buscar músicas de um gênero específico ou limitar a quantidade de itens retornados. 

Complementando os métodos e parâmetros, os `headers` HTTP transmitem metadados, como autenticação ou tipo de conteúdo. Enquanto isso, os códigos de status indicam resultados: 2xx para sucesso (como `200 OK`), 4xx para erros do cliente (como o famoso `404 Not Found`) e 5xx para falhas do servidor (como `500 Internal Server Error`). Esses códigos ajudam a identificar rapidamente problemas, como um usuário tentando acessar uma página inexistente.

Para ser considerada RESTful, uma API deve seguir os seguintes princípios:

- Arquitetura Cliente-Servidor: separação clara de responsabilidades entre cliente e servidor;
- Stateless (Sem Estado): cada requisição deve ser autossuficiente, contendo todas as informações necessárias para seu processamento, sem que o servidor armazene contexto entre requisições;
- Cacheabilidade: clientes ou intermediários podem reutilizar respostas anteriores para requisições idênticas, reduzindo a carga no servidor e melhorando o desempenho (isso deve ser especificado pelo servidor);
- Sistema em Camadas: intermediários (como gateways e balanceadores de carga) podem atuar entre cliente e servidor sem afetar a comunicação, sem que o cliente precise saber disso;
- Interface Uniforme: a interação entre cliente e servidor é padronizada, aderindo a quatro subprincípios:
  - Identificação de Recursos em Requisições: cada recurso envolvido na interação deve ser identificado de maneira única por um URI, sendo conceitualmente distintos das representações retornadas ao cliente;
  - Manipulação de Recurso Através de Representações: se um cliente possui uma representação de um recurso e seus metadados, ele tem informações suficientes para modificar ou excluir o recurso;
  - Mensagens Autodescritivas: mensagens devem incluir informações suficientes para descrever como processá-las;
  - Hipermídia como Motor do Estado de Aplicação (HATEOAS): tendo acessado um URI inicial da aplicação, o cliente deve podem acessar todos os recursos que precise através de links providos pelo servidor.

A seguir está um exemplo de troca de mensagens REST:

```http
GET /musicas/1234 HTTP/1.1
Host: api.com
Accept: application/json
```

```json
// HTTP/1.1 200 OK
// Content-Type: application/json

{
  "id": "1234",
  "titulo": "Purity Weeps",
  "artista": "Invent Animate",
  "lancamento": "Heavener",
  "duracao": "04:08",
  "generos": ["Metalcore", "Metal Progressivo"],
  "_links": {
    "self": { "href": "/musicas/1234" },
    "album": { "href": "/lancamentos/heavener" },
    "artista": { "href": "/artistas/4321" }
  }
}
```

Para facilitar a documentação e padronização de APIs REST, ferramentas como OpenAPI (antigo Swagger) são amplamente usadas. Elas permitem descrever endpoints, métodos e parâmetros em um formato estruturado, possibilitando gerar documentação, código, casos de teste, ect. Isso ajuda a reduzir erros e acelerar o desenvolvimento.

### GraphQL

### WebSocket

### Webhook

## Referências

1. [API // Dicionário do Programador - Youtube](https://youtu.be/vGuqKIRWosk?si=umEoamAHZRe0Otd4)

2. [APIs for Beginners - How to use an API (Full Course / Tutorial) - Youtube](https://youtu.be/WXsD0ZgxjRw?si=zsrBGSIdyCh1_wgv)

3. [API - Wikipedia](https://en.wikipedia.org/wiki/API)

4. [API Collections em Java: fundamentos e implementação básica - DevMedia](https://www.devmedia.com.br/api-collections-em-java-fundamentos-e-implementacao-basica/28445)

5. [Built-in React APIs - React](https://react.dev/reference/react/apis)

6. [Top 6 Most Popular API Architecture Styles - YouTube](https://youtu.be/4vLxWqE94l4?si=dVwWvpkeA3E04J_5)

7. [Difference Between REST API vs Web API vs SOAP API Explained - YouTube](https://youtu.be/2mqN7ZhDsUA?si=68YaT2LbSwbMZXGE)

8. [REST vs SOAP | Differences between SOAP and Rest Web Services | NodeJS Training | Edureka - YouTube](https://youtu.be/_fq8Ye8kodA?si=rapL5smiCPF6WTan)

9. [What Is a SOAP API and How Does It Work? | Postman Blog](https://blog.postman.com/soap-api-definition/#:~:text=SOAP%20\(also%20known%20as%20Simple,text%2C%20JSON%2C%20and%20more.)

10. [RESTful APIs in 100 Seconds // Build an API from Scratch with Node.js Express - YouTube](https://youtu.be/-MTSQjw5DrM?si=wqC1AaDuNdw6p7Zn)

11. [What Is REST API? Examples And How To Use It: Crash Course System Design #3 - YouTube](https://youtu.be/-mN3VyJuCjM?si=4JbcaOw4D4fpREE8)

12. [REST - Wikipedia](https://en.wikipedia.org/wiki/REST)

13. [Fielding Dissertation: CHAPTER 5: Representational State Transfer (REST)](https://ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)

14. [OpenAPI Specification - Wikipedia](https://en.wikipedia.org/wiki/OpenAPI_Specification)

15. [GraphQL Explained in 100 Seconds - YouTube](https://youtu.be/eIQh02xuVw4?si=H0VpdCOQaes73XSs)

16. [GraphQL | A query language for your API](https://graphql.org/)
