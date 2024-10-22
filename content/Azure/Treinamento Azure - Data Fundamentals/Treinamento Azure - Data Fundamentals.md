---
tags:
  - azure
  - cloud
---
> Dia: 13/07/2022

---

### Agenda
Parte 1
1. Introdução
2. Explorar os principais conceitos de dados
3. Explorar dados relacionais no Azure (segmento 1 de 2)
4. Explorar dados relacionais no Azure (segmento 2 de 2)

---

### Recursos
- https://docs.microsoft.com/en-us/learn/certifications/azure-data-fundamentals/
- https://docs.microsoft.com/en-us/learn/certifications/exams/dp-900
- https://docs.microsoft.com/en-us/learn/certifications/azure-database-administrator-associate/
- https://docs.microsoft.com/en-us/azure/azure-sql/database/connectivity-architecture?view=azuresql

---

## Anotações da aula

### Batch data / streaming data

![[Pasted image 20220713141856.png]]

Batch
* No batch se falhar um registro, todo o resto falha
* Grande número de dados

Streaming
* Pequeno volume de dados

### Roles / cargos do banco de dados
![[Pasted image 20220713142434.png]]

* [[Database administrator]]
* Data Engineer
* [[Data Analyst]]


### Conceitos básicos

* Normalização: conjuntos de regras 
	* Primary key e foreign key
	* Sem duplicação de dados
	* Dados são retornados através queries (join)

- Index
	- Optimiza pesquisas