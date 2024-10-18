# Relatório do Seminário
Este documento é um relatório  sobre a apresentação do conteúdo de Banco de Dados e SQL.

### 1. Operadores de Agregação
Operadores de agregação permitem realizar cálculos em um conjunto de dados, como somas, médias e contagens. Eles são essenciais em consultas SQL que exigem análises estatísticas de dados.

- SUM: Calcula a soma de todos os valores numéricos de uma coluna. Útil para totalizar quantidades ou preços.

Exemplo:

    SELECT SUM(preco) FROM produtos;


- COUNT: Conta o número de registros em uma coluna ou tabela. Pode contar registros específicos ou todos os registros.

Exemplo:

    SELECT COUNT(*) FROM clientes;


- MIN e MAX: Identificam o menor e o maior valor em um conjunto de dados.
- MIN: Retorna o valor mínimo de uma coluna.
- MAX: Retorna o valor máximo de uma coluna.

Exemplo:

    SELECT MIN(idade), MAX(idade) FROM alunos;

---

### 2. Joins em SQL
Joins permitem combinar registros de duas ou mais tabelas em uma consulta, com base em uma relação entre colunas.

- INNER JOIN: Retorna os registros que têm correspondência em ambas as tabelas. Se não houver correspondência, o registro não é retornado.

Exemplo:

    SELECT clientes.nome, pedidos.valor 
    FROM clientes 
    INNER JOIN pedidos ON clientes.id = pedidos.cliente_id;

- EFT JOIN: Retorna todos os registros da tabela à esquerda, independentemente de haver correspondência na tabela à direita.

Exemplo:

    SELECT clientes.nome, pedidos.valor 
    FROM clientes 
    LEFT JOIN pedidos ON clientes.id = pedidos.cliente_id;


- RIGHT JOIN: Retorna todos os registros da tabela à direita, com correspondências ou valores nulos da tabela à esquerda.

Exemplo:


    SELECT clientes.nome, pedidos.valor 
    FROM clientes 
    RIGHT JOIN pedidos ON clientes.id = pedidos.cliente_id;


- FULL OUTER JOIN: Retorna todos os registros de ambas as tabelas, mesmo sem correspondência.

Exemplo:

    SELECT clientes.nome, pedidos.valor 
    FROM clientes 
    FULL OUTER JOIN pedidos ON clientes.id = pedidos.cliente_id;
  
