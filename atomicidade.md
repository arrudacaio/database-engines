
## Atomicidade 

* Todas as queries em uma transaction devem ter sucesso.
* Se uma query falhar, todas as queries que funcionaram na transaction DEVEM sofrer ROLLBACK.
* Se o banco de dados tiver um crash durante o commit de uma transaction, todas as queries que rodaram DEVEM sofrer ROLLBACK.
* Atomicidade diz respeito à algo indivisível. Ou é X ou não é -> Houve update no banco de dados ou não houve, não existe meio termo quando estamos tratando de atomicidade.


### Exemplo 

```sql

create table products(
	pid serial primary key,
	name text,
	price float,
	inventory integer
);

create table sales (
	saleid serial primary key,
	pid integer, 
	price float, 
	quantity integer
);

insert into products(name, price, quantity) values ('Phone', 999.99, 100);

begin transaction;
update products set inventory = inventory - 10;
-- Vamos supor que ocorreu algum crash na máquina neste exato momento
-- Isso significa que quando a máquina voltar a funcionar o update não terá sido realizado
-- pois não ocorreu o commit da transaction. Isto é um exemplo de atomicidade, onde todas as queries em uma transaction devem ter sucesso, 
-- se uma falhar, todas as outras queries devem sofrer rollback


```
