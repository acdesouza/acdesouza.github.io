---
layout: post
title: "IndexedDB: Banco de dados no browser"
tags:
- skilled
- javascript
- html5
---
Temos algumas alternativas para gravar dados no lado do cliente, em uma aplicação web.
A estratégia, provavelmente, mais usada é o Cookie. Mas, a limitação de espaço fizeram surgir outras soluções.
Entre elas o [Web SQL Database](http://www.w3.org/TR/webdatabase/), [WebStorage](http://www.w3.org/TR/webstorage/) e o IndexedDB.
[O IndexedDB é um banco de dados do tipo chave-valor com API assincrona, especificado pelo W3C](http://www.w3.org/TR/IndexedDB/).

Estou trabalhando em um projeto de terminal de auto-atendimento, feito em Delphi
com banco de dados PostgreSQL, que centraliza as informações em uma aplicação PHP.

Dentro da lista de requisitos temos:

  * Precisa funcionar offline;
  * Sincronismo entre os terminais, em mesmo cliente;
  * Independência de plataforma, uma vez que a versão atual só roda no Windows;
  * Automatizar o processo de atualização.

O time decidiu fazer um teste com uma aplicação web que gravaria os dados localmente usando um
banco de dados em JavaScript. Vimos que a W3C fez algumas especificações para armazenamento local.
Dentre elas temos: WebStorage, Web SQL Database e IndexedDB.

O WebStorage tem a melhor API. O ponto fraco é que o tamanho dos dados varia de acordo com o navegador usado.
[Inclusive tem um site que testa o tamanho permitido](http://dev-test.nemikor.com/web-storage/support-test/).

O Web SQL Database é lindo. Só que um impasse fez com que a W3C descontinuasse a especificação.
Basicamente, todos os fabricantes de navegadores, estão usando o SQLite para implementar essa especificação.
E, para conseguir avançar no processo de padronização é necessário implementações independentes.


O IndexedDB, foi minha escolha, porque ele não sofre com a limitação do WebStorage.
O inconveniente é que, como disse antes, a API é assincrona, o que significa que ao invés de você pedir
os dados para o banco, esperar o retorno e manipular os dados, você pede os dados e passa uma function
que será executada quando os dados forem recuperados.

Se você nunca viu código funcional, provavelmente vai achar essa forma de desenvolvimento um tanto alienígina.

O (projeto de referência para estudo do IndexedDB)[https://github.com/acdesouza/study_indexeddb] está no GitHub.
É, basicamente, um CRUD onde exercíto as principais operações do banco e defino uma forma de arrumar o código.

Funciona da seguinte forma:

  1. Ao abrir a página:
    1. O banco é criado, caso não exista, e migrado para a última versão disponível
    1. Leio todos os registros, previamente gravados, e exibo em uma tabela
  1. Ao preencher os campos e clicar Gravar:
    1. Adiciona uma nova entrada no banco de dados
    1. Exibe a nova entrada na tabela com botões para editar e excluir
  1. Ao pressionar o botão de editar:
    1. Preenche o formulário com os dados do consumidor, incluindo o id
    1. Ao pressionar o botão de Gravar, ele irá sobrescrever o existente, por ter passado um id existente
    1. Atualiza a linha com os dados novos
  1. Ao pressionar o botão de excluir:
    1. Remove a entrada associada ao id
    1. Remove a linha, na tabela, referente ao id

## Criação do banco de dados

Como disse no início o IndexedDB é um banco de dados do tipo chave-valor, portanto não tem tabelas.
Ainda assim é necessário criar as Object Stores que é o nome dados aos conjuntos distintos de dados. Isto é,
quando eu pedir o id 1, do conjunto de dados de clientes ele não vai me trazer um pedido.

A busca é feita baseada em índices. Que também devem ser explicitamente criados.

A criação das Object Stores e dos Indexes é feita no momento de conexão com com o banco.

E, essa criação é versionada, usando um número inteiro. Assim, quando uma aplicação é
atualizada(refresh no navegador) ele sabe como mudar o banco para a última versão.

{% highlight javascript %}
var database = function() {
var databaseName = "IndexedDbApp";
var version = 1;
var db = null;

var requestCreateDatabase = indexedDB.open(databaseName, version);
requestCreateDatabase.onupgradeneeded = function(event) {
    var db = requestCreateDatabase.result;
    if (event.oldVersion < 1) {
        console.log("[DEBUG] Creates custumers object store.");
        var custumers = db.createObjectStore("custumers", {keyPath: "id", autoIncrement: true});
    }
};
requestCreateDatabase.onsuccess = function() {
    var db = requestCreateDatabase.result;
    db.close();
};
{% endhighlight %}
[javascripts/application.js#L2-L18](https://github.com/acdesouza/study_indexeddb/blob/master/javascripts/application.js#L2-L18)

## Abrir o banco de dados

Qualquer operação com banco de dados é feita após abrir o banco.

{% highlight javascript %}
function open(options){
    var requestOpenDb = indexedDB.open(databaseName, version);

    requestOpenDb.onsuccess = function() {

        var db = requestOpenDb.result;
        var tx = db.transaction(options.objectStoreName, "readwrite");
        var store = tx.objectStore(options.objectStoreName);

        var requestedOperation = options.operation(store);
        if( requestedOperation !== undefined ) {
            requestedOperation.onsuccess = function(e) {
                options.success(e.target.result);
            };
        }

        tx.oncomplete = function(e) {
            db.close();
        };
    };
};
{% endhighlight %}
[javascripts/application.js#L20-L40](https://github.com/acdesouza/study_indexeddb/blob/master/javascripts/application.js#L20-L40)


Fonte: http://www.w3.org/TR/IndexedDB/#opening

## Gravar dados em um Object Store

Uma característica deste banco é que a operação de gravação dos dados não diferencia
se o registro é novo ou já existente. A diferença é se você passou um id existente, ou não.
Na ObjectStore que criamos, o id será auto-increment.

Assim sendo, não temos CREATE e UPDATE como operações sepradas. O que significa que
devemos prestar atenção para não sobrescrever um registro existente.

Pela API ser assíncrona eu recebo callbacks em todas as operações.

{% highlight javascript %}
function open(options){
    var requestOpenDb = indexedDB.open(databaseName, version);

    requestOpenDb.onsuccess = function() {

        var db = requestOpenDb.result;
        var tx = db.transaction(options.objectStoreName, "readwrite");
        var store = tx.objectStore(options.objectStoreName);

        var requestedOperation = options.operation(store);
        if( requestedOperation !== undefined ) {
            requestedOperation.onsuccess = function(e) {
                options.success(e.target.result);
            };
        }

        tx.oncomplete = function(e) {
            db.close();
        };
    };
};
{% endhighlight %}
[javascripts/application.js#L43-L60](https://github.com/acdesouza/study_indexeddb/blob/master/javascripts/application.js#L43-L60)


## Apagar dados em um Object Store

Para apagar um registro, basta passar o id dele, no ObjectStore.

{% highlight javascript %}
destroy: function(objectStoreName, id, callbacks) {
    console.log("[DEBUG] delete, on objectStore: ["+ objectStoreName +"], id: "+ id +".");
    open({
        objectStoreName: objectStoreName,
        operation: function(store) {
            return store.delete(id);
        },
        success: function(id) {
            callbacks.success();
        }
    });
},
{% endhighlight %}
[javascripts/application.js#L62-L73](https://github.com/acdesouza/study_indexeddb/blob/master/javascripts/application.js#L62-L73)

## Ler dados de um ObjectStore

A leitura dos dados, como tudo nesta API, é assíncrono. Isso significa que não dá pra pedir
os dados, colocar eles em uma variável e manipular essa vaiável.

Por conta disso, pensei em um método que aplica uma function para cada dado recebido. Aqui, uso
para montar a lista com todos os registros cadastrados.

Neste caso o a function "success", que está no objeto "callbacks" é chamada a cada iteração com o cursor
e, aplicada ao elemento associado ao cursor.

{% highlight javascript %}
forEachIn: function(objectStoreName, callbacks) {
    console.log("[DEBUG] forEachIn objectStore: ["+ objectStoreName +"].");
    open({
        objectStoreName: objectStoreName,
        operation: function(store) {
            // Get everything in the store;
            var keyRange = IDBKeyRange.lowerBound(0);
            var cursorRequest = store.openCursor(keyRange);

            cursorRequest.onsuccess = function(e) {
                var result = e.target.result;
                if(!!result == false)
                    return;

                var element = result.value;
                console.log("[DEBUG] forEachIn - value: [");
                console.log(element);
                console.log("]");
                callbacks.success(element);

                result.continue();
            };
        }
    });
}
{% endhighlight %}
[javascripts/application.js#L75-L99](https://github.com/acdesouza/study_indexeddb/blob/master/javascripts/application.js#L75-L99)

## Gostaria de saber mais?

  * [W3C IndexedDB](http://www.w3.org/TR/IndexedDB)
  * [JavaScript TODO List](http://www.html5rocks.com/pt/tutorials/indexeddb/todo/)
  * [Experimento para esutar o IndexedDB](https://github.com/acdesouza/study_indexeddb)
