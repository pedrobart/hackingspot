***
# Tópico 1

- **Modelo DIC (Dados / Informação / Conhecimento)**
- **Evolução dos Sistemas de Armazenamento de Dados**
- **Sistemas baseados em ficheiros**
- **Sistemas de bases de dados**
- **Evolução dos Modelos de Bases de Dados**
- **Modelos de bases de dados relacionais**
- **Modelos de bases de dados não relacionais**




## Modelo DIC
***

| Dados                                                                                            | Informação            | Conhecimento                            |
| ------------------------------------------------------------------------------------------------ | --------------------- | --------------------------------------- |
| Qualquer tipo de factos ou observações não interpretados que podem ser armazenados num dado meio | Dados com significado | Informação com aplicação prática ou uso |

## Exemplo


| Dados                           | Informação                                          | Conhecimento                                |
| ------------------------------- | --------------------------------------------------- | ------------------------------------------- |
| **17, 16, 19, 16, 18, 15, 17.** | **O 1º aluno tem 17 anos, o 2º aluno tem 16 anos.** | **O 3º e o 5º aluno são maiores de idade.** |


***


# Sistemas baseados em ficheiros
  ![Pasted image 20240308190348 1](https://github.com/pedrobart/hackingspot/assets/87336174/1a1bc5d4-c969-405b-a7fa-8602d511d9f2)

# Sistemas de bases de dados
![Pasted image 20240308190433 1](https://github.com/pedrobart/hackingspot/assets/87336174/b81ccee5-0e0f-481a-bbce-6a466bf58987)

***
# **Abordagem baseada em ficheiros**

 - **Separação e isolamento da informação**
	- **Cada aplicação mantém o seu próprio conjunto de dados.** 
	- **Os utilizadores de uma aplicação podem não estar cientes da existência de informação potencialmente útil noutras aplicações.**


- **Duplicação de dados**
	- **A mesma informação é mantida por diferentes aplicações.** 
	- **Espaço desperdiçado.** 
	- **Dados potencialmente diferentes (perda de integridade da informação).** 
	- **Os mesmos dados podem estar em diferentes formatos.**


- **Dependência dos dados**
	- **Estrutura do ficheiro é definido no código das aplicações.** 
	- **Qualquer alteração numa estrutura existente é extremamente difícil de ser realizada.**


- **Formatos de ficheiros incompatíveis**
	  **- As aplicações são escritas em linguagens diferentes e, por isso, não podem facilmente aceder a ficheiros de outras aplicações.**
	  **- Fazer corresponder campos de dois ficheiros exige uma outra aplicação para converter os ficheiros em algum formato comum que possibilite o processamento.**


- **As consultas à informação são predefinidas.**
	- **Programas são escritos para satisfazer funções específicas.** 
	- **Qualquer novo requisito precisa de uma nova aplicação.** 
	- **Origina a proliferação de aplicações e ficheiros, muitas vezes omitindo certas funcionalidades:**
		- **Segurança e a integridade da informação.** 
		- **Recuperação limitada ou inexistente (em caso de falha de hardware ou software) .** 
		- **O acesso aos ficheiros é restrito a um utilizador de cada vez sem provisão para acesso partilhado.**

*******
# **Abordagem por Bases de Dados**


**Resolve as limitações dos sistemas baseados em ficheiros.**
![Pasted image 20240308192208 1](https://github.com/pedrobart/hackingspot/assets/87336174/44d07ed7-1482-40d8-97a7-4f21e75b8c2a)



# Conceitos básicos 

| **Base de Dados (BD)**                                                                                                                 | **Sistema de Gestão de Base de Dados (SGBD)**                                                                                                           | **Aplicação de BD**                                                                                               | **Sistema de Base de Dados (SBD)**                                                                         |
| ---------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| **É uma coleção de dados relacionados entre si e que se encontram armazenados e organizados de forma a serem acedidos e manipulados.** | **software que permite criar e manipular uma base de dados de forma a que os utilizadores possam armazenar, processar e analisar os dados facilmente.** | **é um software que interage com a BD por meio da emissão de um pedido (tipicamente uma instrução SQL) ao SGBD.** | **sistema que engloba a base de dados, o sistema de gestão de bases de dados e os aplicativos de acesso.** |

***
# Bases de dados

**As características de utilização influenciam a forma como o sistema de base de dados é implementado e gerido!**

| Supermercado                    | Biblioteca                   | Biblioteca                      | Na internet                                        | Numa linha de produção                     |
| ------------------------------- | ---------------------------- | ------------------------------- | -------------------------------------------------- | ------------------------------------------ |
| quando pagamos as nossas compra | quando requisitamos um livro | quando gerimos o nosso dinheiro | quando realizámos um registo, um login, uma compra | para controlar todas as etapas de produção |
## **Uma base de dados permite assegurar a qualidade dos dados, de modo a disponibilizar informação:**

- **Atual → informação o mais atualizada possível;** 
- **Correta → validação constante da informação;** 
- **Relevante → filtrar a informação;**
- **De uma forma rápida → valoriza a tomada de decisão;** 
- **Legível → fácil interpretação por qualquer utilizador.**

 ==**Uma base de dados possibilita que seja utilizada em simultâneo por vários utilizadores==

***
# Principais Vantagens dos SGBD

- **Controlo da redundância dos dados;**
- **Consistência dos dados;** 
- **Mais informações a partir da mesma quantidade de dados;** 
- **Partilha de dados;** 
- **Melhor integridade de dados;** 
- **Maior segurança;** 
- **Aplicação de normas.**


***
# Principais Desvantagens dos SGBD

- **Maior complexidade;** 
- **Maior custo do SGBD; 
- **Custos de conversão; 
- **Maior impacto quando ocorre uma falha.**

***

# Intervenientes em ambientes SGBD


| Administradores de dados                                                           | Administradores de BD                                                                  | Designers lógico                                                         | Designers físico                                    | Desenvolvedores de aplicações               | Utilizadores finais              |
| ---------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ | --------------------------------------------------- | :------------------------------------------ | :------------------------------- |
| gerem os recursos de dados, como o planeamento da BD e o desenho conceptual/lógico | implementam, fisicamente, a BD e garantem a segurança, integridade e manutenção da BD. | identificam os dados, os relacionamentos entre eles e as suas restrições | efetuam o mapeamento do design lógico para o físico | que interagem com o SGBD e os utilizadores. | correspondemaos “clientes” da BD |

***
# Modelo de dados

- **Um modelo é uma representação de objetos e eventos do mundo real, e as suas associações.** 

- **O propósito de um modelo de dados é representar os dados e os seus relacionamentos;** 

- **Existem vários modelos de bases de dados obsoletos como o modelo em Hierárquico e em Rede;** 

- **O modelo mais utilizado continua a ser o modelo relacional;**** 

- **Novas abordagens estão a emergir (O-R, O-O, NoSQL, …)**

***
# Modelo relacional


![Pasted image 20240308203438 1](https://github.com/pedrobart/hackingspot/assets/87336174/4bf4870c-5837-45ba-9de1-9599b5b83699)

**Os dados são separados por entidades, de acordo com o assunto, e registados como atributos dessas entidades.** 

**Por sua vez, as entidades estabelecem relacionamentos entre si.** 

**Uma entidade é um objeto distinto (pessoa, lugar, coisa, conceito, evento) na organização que é ser representado na BD.** 

**Um atributo é uma propriedade que descreve algum aspeto da entidade. 

Um relacionamento é uma associação entre entidades.**


***
# Modelo NÃO relacional

- **O modelo de bases de dados relacional não é adequado para um sistema distribuído em várias máquinas. As bases de dados NoSQL fornecem uma solução mais viável, concentrando-se em desempenho e disponibilidade, além de sacrificar parte da consistência normalmente identificada com as bases de dados relacionais.** 

- **NoSQL (Not SQL or Not Only SQL) é um termo usado para bases de dados que não dependem de um modelo relacional.**

- **Os dados não necessitam de ter um esquema nem uma estrutura de tabelas SQL. 

- NoSQL permite ter grandes volumes de dados não estruturados e estruturá-los mais tarde.**

![Pasted image 20240308204437 1](https://github.com/pedrobart/hackingspot/assets/87336174/51d35277-d33f-4138-b84d-f5c7e026546e)


***
# Modelo NÃO relacional

## [**Key-value Stores** ](https://aws.amazon.com/pt/nosql/key-value/)

- **Baseado em [distributed hash tables](https://hazelcast.com/glossary/distributed-hash-table/) e [Dynamo paper](https://www.dynamodbguide.com/the-dynamo-paper/) da Amazon.** 

- **Criado para manipular quantidades massivas de dados e armazenar dados não esquematizados.**

- **Inserção e obtenção de dados é simples** 

- **Armazena dados em tabelas hash com chaves únicas.**

- **As chaves podem ser armazenadas como strings, lists, hashes sets, sorted sets, json, blob, etc.** 
- **Os valores podem ser armazenados como collections, associative arrays, and dictionaries, etc.** 

**Exemplos: [Redis](https://aws.amazon.com/pt/elasticache/what-is-redis/), [Memcached](https://aws.amazon.com/pt/memcached/)**
![Pasted image 20240308205912 1](https://github.com/pedrobart/hackingspot/assets/87336174/c78eab71-eb8f-463d-b029-e7a506a01437)



***
# Modelo NÃO relacional

## **Document Stores** 

- **Coleções de documentos.** 

- **Cada documento é independente.** 

- **Documentos são livres de esquema e fáceis de modificar.** 

- **Coleções são usadas para armazenar documentos e para agrupar diferentes tipos de dados. Documentos podem conter outros documentos, diferentes pares de chave-valor ou chave-array.** 

### **Exemplos**
**[MondoDB](https://www.mongodb.com/why-use-mongodb), [Couchbase](https://developer.couchbase.com/what-is-couchbase/), [RavenDB](https://ravendb.net/)**
***
# Modelo NÃO relacional

## Column Oriented 

- **Os dados são armazenados em colunas com o mesmo tipo de dados e cada coluna é tratada separadamente.** 
 
- **Processamento de [queries](https://www.hostinger.pt/tutoriais/o-que-e-query) é feito nas colunas e melhora a sua performance porque acede a dados específicos de cada coluna.** 

**São desenhadas como arrays tridimensionais:** 
- **identificador da linha**
- **identificador da coluna e sua família** 
- **selo temporal.** 

**Exemplos** 
[Apache Cassandra](https://cassandra.apache.org/_/index.html), [Hadoop Hbase](https://hbase.apache.org/), [HyperTable](https://hypertable.com/documentation/)**


![Pasted image 20240309001622 1](https://github.com/pedrobart/hackingspot/assets/87336174/e875058a-77f8-41af-a849-21fbe7625e6b)

***
# Modelo NÃO relacional

## Graph Network 

- **Os dados são armazenados em estruturas de grafos.** 
- **São usadas para dados com alta taxa de atualização.** 
- **Representam qualquer tipo de dados, têm alta acessibilidade e usam índices para procura.** 
- **É um coleção de e um ou mais nós (nodes) e arcos (edges).** 
- **Cada nó representa uma entidade (estudante, disciplina).** 
- **Cada arco liga dois nós e representa a sua relação.** 
- **Cada Nó e Arco tem o seu identificador único.**** 
**
### Exemplos 
**[FlockDB](https://github.com/twitter-archive/flockdb), [HyperGraphDB](https://hypergraphdb.org/), [Neo4j](https://neo4j.com/docs/)**
![Pasted image 20240309002337 1](https://github.com/pedrobart/hackingspot/assets/87336174/2711b36e-b2fd-4b43-bfac-7473420bceac)

***
# Modelo NÃO relacional

## Hierarchical 

- **Usa relações Pai-Filho ou estruturas em árvore para armazenar os dados.** 

- **Nos modelos relacionais, isto é designado como uma relação UM-para-MUITOS.** 

- **Informação de localização é armazenada em bases de dados geo-espaciais.** 

**Exemplos** 
**[PostGIS](https://postgis.net/), [Oracle Spatial](https://www.oracle.com/database/spatial/)**
![Pasted image 20240309003038 1](https://github.com/pedrobart/hackingspot/assets/87336174/304448dd-3481-44e5-9f7c-1f8d1ae446ce)

***
# Modelo NÃO relacional

## Object-Oriented 

- **Dados são armazenados em forma de objetos.** 

- **Estrutura destas bases de dados é diferente dos RDBMS tradicionais** 

**Exemplos** 
**[db4o](http://www.db4o.com/), [NEO](https://neo.nexedi.com/), [Versant](http://www.versant.com/)**
![Pasted image 20240309003312 1](https://github.com/pedrobart/hackingspot/assets/87336174/e0cf7379-5c74-4d3a-82f0-69c3b0df5503)


***
# Modelo NÃO relacional

	## Triple Stores 

- **Gere os dados na forma de “Sujeito-Predicado-Objeto”.** 
- **O predicado é usado para ligar o Sujeito com o Objeto.** 
- **São uma variante das Network Databases.** 

Exemplos 
[Sesame](https://www.lanl.gov/org/ddste/aldsc/theoretical/physics-chemistry-materials/sesame-database.php), [Jena](https://jena.apache.org/), [Virtuoso](https://virtuoso.openlinksw.com/), [Allegro Graph](https://allegrograph.com/)
***
# Relacional versus Não Relacional
![Pasted image 20240309004204 1](https://github.com/pedrobart/hackingspot/assets/87336174/8b035ff3-3127-4239-b61b-3eb92abdd671)

***
# Tópico 2

- **Ciclo de Vida dos Sistemas de Base de Dados**
- **Modelo Entidade-Relacionamentos:**
	- **Metodologia de construção;**
	- **Entidades, Relacionamentos e Atributos;**
	- **Diagramas E/R;**
	- **Notação Chen;**
