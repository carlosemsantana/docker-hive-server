# Apache Hive™

Apache Hive™ é um software de Data Warehouse desenvolvido em cima do Apache Hadoop para consulta e análise de dados. O Hive oferece uma interface semelhante ao SQL para consulta de dados em diferentes bancos de dados e sistemas de arquivos integrados ao Hadoop.

O Apache Hive™ facilita a leitura, consulta, gravação e gerenciamento de grandes conjuntos de dados distribuídos.

Construído sobre o Apache Hadoop™, o Hive oferece os seguintes recursos:

- Ferramentas para facilitar o acesso aos dados via SQL, permitindo assim tarefas de armazenamento de dados, como extrair/transformar/carregar (ETL), relatórios e análise de dados;
- Um mecanismo para importar estruturas em uma variedade de formatos de dados;
- Acesso a arquivos armazenados diretamente no Apache HDFS ™ ou em outros sistemas de armazenamento de dados, como o Apache HBase™;  
- Execução de consultas via Apache Tez™ , Apache Spark™ ou MapReduce;
- Linguagem procedural com HPL-SQL;
- Recuperação de consulta em menos de um segundo via Hive LLAP, Apache YARN e Apache Slider; 

Hive fornece funcionalidade SQL padrão, incluindo muitos dos SQL:2003, SQL:2011 e SQL:2016 para análise.
O SQL do Hive também pode ser estendido com código do usuário por meio de funções definidas pelo usuário (UDFs), agregações definidas pelo usuário (UDAFs) e funções de tabela definidas pelo usuário (UDTFs).

Não existe um único "formato Hive" no qual os dados devem ser armazenados. O Hive vem com conectores integrados para arquivos de texto com valores separados por vírgula e tabulação (CSV/TSV), Apache Parquet™, Apache ORC™ e outros formatos. Os usuários podem estender o Hive com conectores para outros formatos. Consulte Formatos e Hive SerDe no Guia do desenvolvedor para obter detalhes.

O Hive não foi projetado para cargas de trabalho de processamento de transações online (OLTP). É melhor usado para tarefas tradicionais de armazenamento de dados.

O Hive foi projetado para maximizar a escalabilidade (escalar horizontalmente com mais máquinas adicionadas dinamicamente ao cluster Hadoop), desempenho, extensibilidade, tolerância a falhas e acoplamento flexível com seus formatos de entrada.

Os componentes do Hive incluem HCatalog e WebHCat. 

- O HCatalog é uma camada de gerenciamento de tabela e armazenamento para Hadoop que permite que usuários com diferentes ferramentas de processamento de dados — incluindo Pig e MapReduce — leiam e gravem dados na grade com mais facilidade.
- O WebHCat fornece um serviço que você pode usar para executar tarefas Hadoop MapReduce (ou YARN), Pig, Hive. Você também pode executar operações de metadados do Hive usando uma interface HTTP (estilo REST).
- HiveServer2 (HS2) - Serviço que permite aos clientes executar consultas no Hive.
    







### Exercícios


1. Enviar o arquivo local “/input/exercises-data/populacaoLA/populacaoLA.csv” para o diretório no HDFS “/user/santana/data/populacao”

```Python
$ docker exec -it namenode bash
$ hdfs dfs -put input/exercises-data/populacaoLA/populacaoLA.csv /user/santana/data/populacao

```

#### Resultado:
<img src="img/hdfs-dfs-put-populacao.png" alt="Envia arquivo local para HDFS">


2. Lista o banco de dados 

```Python
$ docker exec -it namenode bash
$ beeline -u jdbc:hive2://localhost:10000
$ show databases

```

#### Resultado:
<img src="img/beeline.png" alt="Lista o banco de dados">


3.  Criar o banco de dados <nome> 

```Python
$ docker exec -it namenode bash
$ beeline -u jdbc:hive2://localhost:10000
$ create database populacaoLA

```

#### Resultado:
<img src="img/create-database.png" alt="Criar o banco de dados">


4.  Criar a Tabela Hive no BD pessoa

<img src="img/tabela.png" alt="Criar tabela no banco de dados">


```Python
$ create table pessoa (
                zip_code INT,
                total_population INT, 
                median_age INT, 
                total_males INT, 
                total_females INT,   
                total_household_size FLOAT)
                
  ROW FORMAT DELIMITED
  FIELDS TERMINATED BY '\t';
  STORED AS TEXTFILE
  tBLPROPERTIES ("skip.header.line.count"="1");

```

#### Resultado:
<img src="img/create-table-pop.png" alt="Criar tabela">


5. Visualizar a descrição da tabela pop

```Python
$ desc formatted pessoa


```

#### Resultado:
<img src="img/desc-formatted-table.png" alt="Criar o banco de dados">


continua...

```python

```
