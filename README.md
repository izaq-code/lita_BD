--4) Quais os nomes dos departamentos que não possuem gerente?

SELECT Nome as nome_departameno
FROM departamento
WHERE GCPF = 'NULL'

--7) Qual o nome de cada departamento, do seu gerente e a data em que ele se tornou gerente?

SELECT departamento.Nome as nome_departameno,empregado.nome as nome_empregado, departamento.inicio as data_de_inicio
FROM departamento
INNER JOIN empregado ON departamento.GCPF = empregado.CPF

--10) Quais os nomes das esposas dos empregados que trabalham no projeto Alfa?

SELECT dependente.Nome as nome_esposa
FROM empregado
INNER JOIN dependente ON empregado.CPF = dependente.ECPF 
INNER JOIN projeto ON projeto.Cod = empregado.Depto
WHERE dependente.Parentesco = 'C�njuge' AND dependente.sexo = 'F' AND projeto.nome = 'Alfa'

--20) Qual é o valor do salário médio pago pela empresa?

SELECT  ROUND(AVG(Salario), 2) as salario_medio FROM empregado

--21) Qual é o menor valor de orçamento de projeto existente na empresa?

SELECT min(Orcamento) as Orcamento_minimo
FROM projeto

--22) Quais os nomes dos empregados que ganham o maior salário?

SELECT Nome as nome_empregado, salario
FROM empregado
