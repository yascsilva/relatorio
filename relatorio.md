# Relatório do Seminário
Este documento é um relatório  sobre a apresentação do conteúdo de Banco de Dados e SQL.

### 1. Operadores de Agregação
Operadores de agregação permitem realizar cálculos em um conjunto de dados, como somas, médias e contagens. Eles são essenciais em consultas SQL que exigem análises estatísticas de dados.

- **SUM:** Calcula a soma de todos os valores numéricos de uma coluna. Útil para totalizar quantidades ou preços.

**Exemplo:**

    SELECT SUM(preco) FROM produtos;


- **COUNT:** Conta o número de registros em uma coluna ou tabela. Pode contar registros específicos ou todos os registros.

**Exemplo:**

    SELECT COUNT(*) FROM clientes;


- **MIN e MAX:** Identificam o menor e o maior valor em um conjunto de dados.
- **MIN:** Retorna o valor mínimo de uma coluna.
- **MAX:** Retorna o valor máximo de uma coluna.

**Exemplo:**

    SELECT MIN(idade), MAX(idade) FROM alunos;

---

### 2. Joins em SQL
Joins permitem combinar registros de duas ou mais tabelas em uma consulta, com base em uma relação entre colunas.

- **INNER JOIN:** Retorna os registros que têm correspondência em ambas as tabelas. Se não houver correspondência, o registro não é retornado.

**Exemplo:**

    SELECT clientes.nome, pedidos.valor 
    FROM clientes 
    INNER JOIN pedidos ON clientes.id = pedidos.cliente_id;

- **EFT JOIN:** Retorna todos os registros da tabela à esquerda, independentemente de haver correspondência na tabela à direita.

**Exemplo:**

    SELECT clientes.nome, pedidos.valor 
    FROM clientes 
    LEFT JOIN pedidos ON clientes.id = pedidos.cliente_id;


- **RIGHT JOIN:** Retorna todos os registros da tabela à direita, com correspondências ou valores nulos da tabela à esquerda.

**Exemplo:**


    SELECT clientes.nome, pedidos.valor 
    FROM clientes 
    RIGHT JOIN pedidos ON clientes.id = pedidos.cliente_id;


- **FULL OUTER JOIN:** Retorna todos os registros de ambas as tabelas, mesmo sem correspondência.

**Exemplo:**

    SELECT clientes.nome, pedidos.valor 
    FROM clientes 
    FULL OUTER JOIN pedidos ON clientes.id = pedidos.cliente_id;

---

### 3. Operadores Lógicos
Operadores lógicos ajudam a definir condições que uma consulta deve atender para retornar resultados específicos.

- **AND:** Retorna registros quando todas as condições são verdadeiras.

**Exemplo:**

    SELECT * FROM empregados 
    WHERE salario > 3000 AND idade < 40;

- **OR:** Retorna registros quando pelo menos uma das condições é verdadeira.

**Exemplo:**

    SELECT * FROM empregados 
    WHERE salario > 3000 OR idade < 40;

- **NOT:** Inverte a condição, retornando os resultados que não atendem à condição especificada.

**Exemplo:**

    SELECT * FROM empregados 
    WHERE NOT salario > 3000;

- **Combinação de Operadores:** Várias condições podem ser combinadas usando parênteses para controlar a precedência.

**Exemplo:**

    SELECT * FROM empregados 
    WHERE (salario > 3000 AND idade < 40) OR departamento = 'TI';

---

### 4. Subconsultas
Subconsultas são consultas aninhadas dentro de outras consultas. Elas são úteis para executar consultas complexas em partes.

- **Definição e Usos Práticos:** Subconsultas permitem realizar uma consulta dentro de outra.

**Exemplo:**

    SELECT nome FROM empregados 
    WHERE salario > (SELECT AVG(salario) FROM empregados);

- **Subconsultas Correlacionadas:** Dependem de dados da consulta externa e são avaliadas linha a linha.

**Exemplo:**

    SELECT nome FROM empregados e 
    WHERE salario > (SELECT AVG(salario) 
    FROM empregados WHERE departamento = e.departamento);


---

### 5. Funções de Agregação com GROUP BY
O GROUP BY permite agrupar dados em categorias e executar funções de agregação nesses grupos.

- **Agrupamento de Resultados:** Agrupa linhas com base em valores comuns de uma ou mais colunas.

**Exemplo:**


    SELECT departamento, AVG(salario) 
    FROM empregados 
    GROUP BY departamento;

- **Combinação com HAVING:** Filtra os grupos de resultados após a agregação. Diferente do WHERE, que filtra antes da agregação.

**Exemplo:**

    SELECT departamento, AVG(salario) 
    FROM empregados 
    GROUP BY departamento 
    HAVING AVG(salario) > 4000;

---

### 6. Indexação e Performance
Índices melhoram a performance de consultas ao permitir acesso mais rápido aos dados.

- **Impacto da Indexação:** Melhora o desempenho das consultas, especialmente em tabelas grandes.

**Exemplo:** Criar um índice na coluna que é frequentemente usada em filtros.

- **Quando Usar Índices:** Use índices em colunas que são frequentemente usadas em filtros, ordenações ou junções. Evite índices em tabelas pequenas ou em colunas que sofrem muitas atualizações, pois isso pode prejudicar a performance de inserções e atualizações.

---

### 7. Transações e Controle de Confiabilidade
Transações garantem que um conjunto de operações de banco de dados seja tratado como uma unidade atômica.

- **Importância das Transações:** Elas garantem que todas as operações em uma transação sejam bem-sucedidas ou nenhuma delas seja realizada.

**Exemplo:**

    BEGIN TRANSACTION;
    UPDATE contas SET saldo = saldo - 100 WHERE id = 1;
    UPDATE contas SET saldo = saldo + 100 WHERE id = 2;
    COMMIT;

- **COMMIT e ROLLBACK:**

  - **COMMIT:** Confirma todas as operações da transação, tornando as mudanças permanentes.
  - **ROLLBACK:** Reverte todas as operações da transação, restaurando o banco de dados ao estado anterior.
- **Cenários Práticos:** Transações são críticas em sistemas financeiros, como bancos e e-commerce, onde falhas no processo de transação podem levar a inconsistências de dados.
