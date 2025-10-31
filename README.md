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

  **Expressões Aritiméticas:**
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
   
  **Regras de procedência de operadores:**
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

**Entendendo o valor nulo (NULL):**
  - Null é ausência de valorç
  - Null não é zero;
  - Null não é espaços em branco;
  - Null não zeros binários;
  ~~~SQL
    SELECT first_name, last_name, job_id,
    salary, commission_pct
    FROM employess;
  ~~~
  - O SQL retona ```(null)```;

**Utilizando valores nulos em expressões aritméticas:**
  - Qualquer expressão aritmética utilizando NULL retorna Null;
   ~~~SQL
    SELECT first_name, last_name, job_id,
    salary, commission_pct, commission_pct * 1000
    FROM employess
    WHERE commission_pct IS NULL;
  ~~~
  - Então:
    - 10 + NULL = NULL;
    - 10 - NULL = NULL;
    - 10 * NULL = NULL;
    - 10 / NULL = NULL;

**Alias de Coluna:**
  - Renomeia o cabeçalho da coluna;
  - Segue Imediamente o nome da coluna;
  - Opcionalmente pode ser utilizado a palavra chave ```AS``` entre as colunas e o alias;
  - Quando o alias contém espaços, caracteres especias ou for case sensitive(letras maiusculas)então se deve ser colocado entre aspas duplas("");
   ~~~SQL
    SELECT first_name AS "Nome", last_name sobrenome, salary "salário"
    FROM employess
  ~~~

**Operador de concatenação:**
  - Liga colunas ou strings de caracteres com outras colunas ou strings de caractreres;
  - É representado por duas barras verticais(||)
  - Cria uma segunda coluna resultante da ligação que é uma string de caracteres;
  ~~~SQL
    SELECT first_name || ' '  ||  last_name, ', data de admissão: ' || hire_date, "Funcionário" -- alias
    FROM employess     
  ~~~

**Strings de Caracteres:**
  - Um Literal é um caracter, um número, ou uma string  que é incluída em um comando SELECT;
  - Literais de datas e  caracteres devem ser definidos entre aspas simples('');
  - Cada Literal ou string será exibido uma vez para cada linha retornada;

**Operador alternativo para aspas:**
  - Você pode especificar seu próprio operador alternativo para aspas;
  - Escolha qualquer delimitador;
  - Facilita a legibilidade e usabilidade;
  - q é quot que é aspas em inglês;
  - Nesse caso tem que usar ```AS``` para não dar conflito de aspas
  ~~~SQL
    SELECT departament_name || q' [ Departament's Manager Id: ]' ||  manager_id AS "Departamento e Gerente"
    FROM departaments;
  ~~~

**Linhas duplicadas:**
  - Por default as consultas exibem todas as linhas retornadas, incluindo as linhas duplicadas.
   ~~~SQL
    SELECT departament_id
    FROM employees;
   ~~~
  - Esse tipo de retorno vão trazer muitos empregados com ID de departamento duplicadosç;
  - Para trazer o valor de cada departamento uma vez só: com o uso da clausula ```DISTINCT```
   ~~~SQL
    SELECT DISTINCT departament_id
    FROM employees;

    SELECT DISTINCT last_name, first_name -- aqui o distinct é pra query toda
    FROM employees;
   ~~~

## Restringindo e ordenando dados:

**Restringindo as linhas que serão retornadas:**
  - Selecione as linhas que serão retornadas utilisando a cláusula ```WHERE```;
  ~~~SQL
    SELECT *|{[DISTINCT] coluna|expressão [alias], ...}
    FROM tabela
    [WHERE condição(s)];
  ~~~
  ~~~SQL
    SELECT employee_id, last_name, job_id, departament_id
    FROM employees
    WHERE departament_id = 60;
  ~~~

**Strings de caractreres e datas:**
  - Strings de caracteres e datas são delimitados por aspas simples('');
  - Valores de strings de caracteres são case sensitivos;
  - Valores de strings de data são sensitivos ao formato definido para o banco de dados ou para a sessão;
  - O format default para  a exibição de datas mais utilizado no Brasil é ```'DD/MM/YY'```ou ```'DD/MM/RR'```
  ~~~SQL
    SELECT first_name last_name, job_id, departament_id, hire_date
    FROM employees
    WHERE last_name = 'King';
  ~~~
  ~~~SQL
    SELECT first_name, last_name, job_id, departament_id, hire_date
    FROM employees
    WHERE hire_date = '30/01/04';
  ~~~
  | Operador  | Descrição |
  | ------------- | ------------- |
  | = | Igual a |
  | > | Maior que |
  | >= | Maior ou igual |
  | < | Menor que  |
  | <= | Menor ou igual  |
  | <> | diferente |
  | BETWEEN ... AND ... | Entre dois valores |
  | IN(set) | Corresponder a qualquer um dos valores de uma lista |
  | LIKE | corresponder a um padrão de caractere |
  | IS NULL | Valor igual a nulo |

**Utilizando operadores de comparação na cláusula WHERE:**
  ~~~SQL
    SELECT last_name, salary
    FROM employees
    WHERE salary >= 10000;
  ~~~

**Selecionando faixas de valores utilizando o operador BETWEEN:**
  ~~~SQL
    SELECT last_name, salary
    FROM employees
    WHERE salary BETWEEN 10000 AND 15000;
  ~~~

**Selecionado valores dentro de uma lista utilizando o operador IN:**
   ~~~SQL
    SELECT employee_id last_name, salary, manager_id, job_id
    FROM employees
    WHERE job_id IN ('IT_PROG', 'FI_ACCOUNT', 'SA_REP'); -- valores que ele quer buscar
  ~~~

**Selecionado valores dentro de uma lista utilizando o operador LIKE:**
  - Use o operador LIKE para executar pesquisas de valores que coincidem com padrões utilizando caracteres curingas(wildcards);
  - As condições de pesquisa podem conter caracteres ou números:
    - % Combina com zero ou mais caracteres;
    - _ Combina com 1 e somente um caracter;
  ~~~SQL
    SELECT first_name, last_name, job_id
    FROM employees
    WHERE first_name LIKE 'Sa%'; -- no caso o a é seguido de qualquer coisa
  ~~~

**Combinando o uso de vários caracteres curinga:**
  - Exemplo com segunda letra:
  ~~~SQL
    SELECT first_name, last_name
    FROM employees
    WHERE last_name LIKE '_a%'; -- o _ significa um caracter qualquer seguido de a e %(n caracteres quaisquer)
  ~~~
  - Exemplo com ultima letra:
   ~~~SQL
    SELECT first_name, last_name
    FROM employees
    WHERE last_name LIKE '%a'; -- o _ significa um caracter qualquer seguido de a e %(n caracteres quaisquer)
  ~~~

**Comparações com valor nulo:**
  - Qualquer comparação com valor NULL retona o booleano NULL;
  - Para podermos verificar se um valor é NULL deve ser utilizado a expressão IS NULL
  - Nessa pesquisa a seguir não retorna nada:
  ~~~SQL
    SELECT last_name, manager_id
    FROM employees
    WHERE manager_id = NULL;
  ~~~
  - E para resolver:
  ~~~SQL
    SELECT last_name, manager_id
    FROM employees
    WHERE manager_id IS NULL;
  ~~~
