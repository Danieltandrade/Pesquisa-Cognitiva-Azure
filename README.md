# Pesquisa-Cognitiva-Azure

Neste README explicarei um caso de uso da Ferramenta de Pesquisa Cognitiva dentro da Plataforma de __AI Services__ do __Microsoft Azure__. 

## Documentação

Colocarei logo no ínicio o link da documentação que foi utlizada para este laboratório de aprendizado. 

-[Microsoft Azure Machine Learn - Azure AI Search](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/11-ai-search.html)

## Estudo de Caso

Neste laboratório fui solicitado a ajudar na criação de uma solução de mineração de conhecimento que facilite a busca de insights sobre as experiências dos clientes para uma rede de Cafés chamada __Fourth Coffee__.

## Criando Recursos

Para começar, será necessário entrar no [Portal Azure](https://azure.microsoft.com/pt-br/)
Dentro do portal será necessários criar alguns recursos, conforme pedido na documentação.

### Recurso Azure AI Seach

O primeiro recurso criado será com a ferramenta Azure AI Seach. É importante seguir os passos da documentação para que o recurso seja criado da forma correta. O resultado será visto na __Imagem1__ abaixo:

<img src="Arquivos/Imagem1.JPG">Imagem1


### Recurso Azure Ai Service - Serviços Cognitivos

O segundo passo é retornar à página inicial do Azure e clicar em __"+ Criar um recurso"__ e buscar por __"Serviços Cognitivos"__ ou __"Azure AI Services"__, clicando em __"Criar"__. Aqui também é importante seguir os passos da documentação para que o recurso seja criado da forma correta. O resultado será visto na __Imagem2__ abaixo:

<img src="Arquivos/Imagem2.JPG">Imagem2


### Recurso Storage Account - Conta de Armazenamento

O terceiro passo é retornar à página inicial do Azure e clicar em __"+ Criar um recurso"__ e buscar por __"Conta de Armazenamento"__ ou __"Storage Account"__, clicando em __"Criar"__. Como ocorreu nos outros recusrsos, aqui também é importante seguir os passos da documentação para que o recurso seja criado da forma correta. O resultado será visto na __Imagem3__ abaixo:

<img src="Arquivos/Imagem3.JPG">Imagem3


## Upload de Documentos do Azure Storage

Aqui será realizado os passos para criação de um novo __"Container"__ aonde será armazenados os dados. Aqui é importantíssimo seguir a documentação para que seja criado da forma certa. Outro detalhe importante é __"Permitir acesso anônimo de Blob"__ como __"Habilitado"__, conforme __Imagem4__ abaixo:

<img src="Arquivos/Imagem4.JPG">Imagem4


 Após criado o Container é necessário baixar os arquivo no [Zipped Coffee Reviews](https://aka.ms/mslearn-coffee-reviews). Com os arquivos baixados é só realizar o Upload no Container criado, com o resultado igual a __Imagem6__ abaixo:

 <img src="Arquivos/Imagem6.JPG">Imagem6

 ## Indexar os Documentos

Depois de armazenar os documentos, usaremos o __Azure AI Search__ para extrair os insights dos documentos. O portal do Azure fornece um assistente de importação de dados. Com este assistente, criaremos um índice e um indexador para fontes de dados.

Aqui também é de suma importância seguir os passos da documentação para que o índice e o indexador seja crado da forma correta.

Após o Indexador criado, volte à página de recursos do __Azure AI Search__. No painel esquerdo, em __"Gerenciamento de Pesquisa"__, selecione __"Indexadores"__ . Selecione o __"coffee-indexer"__ recém criado.

Selecionando o indexador poderemos ver mais detalhes, conforme __Imagem7__ abaixo:

<img src="Arquivos/Imagem7.JPG">Imagem7


## Realizando Consultas

Podemos usar o __"Search Explorer"__ ou __"Explorador de Pesquisas"__ para escrever consultas e revisar resultados em JSON.

### Filtrando Documentos

```
{
    "search": "*",
    "count": true
}
```

Conforme comando acima, é pedido uma pesquisa que retorna todos os documentos no índice de pesquisa, incluindo uma contagem de todos os documentos no campo __@odata.count__.
O resultado é exbido na __Imagem8__ abaixo:

<img src="Arquivos/Imagem8.JPG">Imagem8


### Filtrando Localização

```
{
 "search": "locations:'Chicago'",
 "count": true
}
```

Conforme comando acima, é pedido uma pesquisa que retorna todos os documentos no índice e filtra revisões com localização em Chicago. O resultado é __3__ no campo __@odata.count__, conforme __Imagem9__ abaixo:

<img src="Arquivos/Imagem9.JPG">Imagem9


### Filtrando Sentimentos

```
{
 "search": "sentiment:'negative'",
 "count": true
}
```

Conforme comando acima, a consulta pesquisa todos os documentos no índice e filtra revisões com sentimento negativo. O resultado é __1__ no campo __@odata.count__, conforme mostrado na __Imagem10__ abaixo:

<img src="Arquivos/Imagem10.JPG">Imagem10


