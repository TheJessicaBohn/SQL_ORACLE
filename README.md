# SQL_ORACLE

## Características do SQL:
  - SQL é uma linguagem padrão para as operações em bancos de dados relacionais;
  - Eficiente, fácil de aprender e utilizar;
  - Funcinalmente completa;
  - Com SQL, é possível definir, consultar e manipular dados em tabelas;

## Ferramentas :
  - Oracle SQL Developer;
  - Oracle SQL * Plus;
  - PL/SQL Developer;
  - Toad;
  - Oracle JDeveloper;
  - Oracle Application Express;
  - Eclipse;
  - NetBeans;
  - Oracle Financials;
  - Oracle Project;
  - Oracle Business Suite;

## Documentação:
  - https://docs.oracle.com/en/database/oracle/oracle-database/index.html

## Outras Linguagens:
  - PL/SQL;
  - Java;
  - C++;
  - PHP;
  - C#;
  - Cobol;
  - etc;

## Oracle SQL x ANSI SQL:
  - SQL ANSI é o SQL padrão estabelecido pelo American National Standards Institute, capaz de rodar em qualquer banco de dados relacional;
  - Oracle SQL é pareciso, mas não é identico ao SQL ANSI;
  - A maioria dos comandos mesmo em Oracle SQL são ANSI;

## Comandos SQL
  **Data Manipulation Language(DML):**
  - SELECT: Recuperar dados;
  - INSERT: Inserir linhas numa tabela;
  - UPDATE: Atualizar linha;
  - DELETE: Deletart linhas de uma tabela;
  - MERGE: Comparar duas tabelas, a origem e a destino e atualizar a tabela destino;

  **Data Definition Language:**
  - CREATE: Criar tabelas, indices visões, sequences;
  - ALTER: Alterar estruturas de tabelas, indices, sequences;
  - DROP: Remover tabelas, indices, sequences;
  - RENAME: Renomear objeto;
  - TRUCATE: para deixar uma tabela vazia;
  - COMMENT: Adiciona um comentário ou documentação;

  **Data Control Language (DCL):**
  - GRANT: Passar privilégios;
  - REVOKE: Revoga privilágios;

  **Transaction Control:**
  - COMMIT: Efetiva uma transação, e ela não poderá mais ser desfeita;
  - ROLLBACK: Desfaz a transação;
  - SAVEPOINT: Cria um ponto de controle na transação;

## Comando SELECT:
  - Comando DESCRIBE: Exibir a estrutura de uma tabela
    - Não é um comando SQL, é um comando do SQL Plus, e do SQL developer
    - DESC[RIBE] tabela;
    ~~~SQL
      DESCRIBE employees;

      DESC departaments;
    ~~~
  - Executar um comando SELET básico:
    ~~~SQL
      SELECT *|{[DISTINCT] coluna|expressão [alias],...}
      FROM tabela;

      SELECT *
      FROM departaments;

      SELECT departament_id, location_id,
      FROM departaments;

      SELECT
        job_id
        job_title
      FROM
        jobs;
    ~~~
    - SELECT identifica as colunas ou expressões a serem exibidas;
    - FROM indentifica as tabelas que contém as colunas;
  - Definir Alias de Coluna:
  - Utilizar strings de cartacteres:
  - Utilizar operador de concatenação:
  - Utilizar o Operador alternativo para áspas:
  - Enternder o uso de DISTINCT:
  - Como o comando SELECT podemos fazer:
    - **Projection**: selecionar Colunas;
    - **Selection**: selecionar as linhas:
    - **Join**: usar colunas de mais de uma tabela
 
  **Escrevendo comandos SQL:**
  - Comandos SQL não são case sensitivos;
  - Comandos SQL podem se extender por uma ou mais linhas;
  - Palavras chave(Keywords) **não podem ser abreviadas** ou divididas através das linhas;
  - Clausulas são normalmente colocadas em linhas separadas;
  - Identação são utilizadas para facilitar o entendimento do comando;
  - Comandos SQL são terminados por ponto e virgula(;), mas no developer não tem essa necessidade, mas se tiver o **;** ele vai sabe que se o cursor estiver na frente ele sabe qual o comando que tem que rodar sem precisar selecionar;

  **Alinhamento de colunas em cabeçalhos:**
  - **Colunas Chacaracter e Date** o alinhamento default do cabeçalho: Esquerda;
  - **Colunas Number** o alinhamento: Direita;
  - **Exibição default do cabeçalho**: Letras maiúsculas;

  **Expressões Aritiméticas:
  - Pode-se criar expressões aritiméticas com números e datas utilizando operadores aritméticos:
    | Operador  | Descrição |
    | ------------- | ------------- |
    | + | Adição  |
    | - | Subtração  |
    | * | Multiplicação  |
    | - | Divisão  |
    ~~~SQL
      SELECT first_name, last_name, salary,
      salary * 1.5
      FROM employess;
    ~~~
    - Nesse exemplo ele retorna as 3 colunas, e a coluna salário é multiplicada por 1,5;
   
  **Regras de procedência de operadores:
  - Mesmas regras de precedência da matematica:
    - 1. Identidade(positivo ou negativo);
    - 2. Multiplicação e divisão (possuem a mesma procedência, resolvendo da esquerda para a direita);
    - 3. Soma e subtração (possuem a mesma procedência, resolvendo da esquerda para a direita);
   ~~~SQL
    SELECT first_name, last_name, salary,
    salary + 100 * 1.5
    FROM employess;
  ~~~
  - Nesse caso ele faz a multiplicação antes e depois a a soma com o salário;
  - Para mudar a precedência é necessário utilizar parenteses **()**;
  ~~~SQL
    SELECT first_name, last_name, salary,
    (salary + 100) * 1.5
    FROM employess;
  ~~~
  - Nesse caso ele soma primeiro e depois faz a multiplicação;
