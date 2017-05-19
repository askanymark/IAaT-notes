# SQL
Structured Query Language


Basic stuff:

```sql
create table tablename(field1 type constraints, field2...);
alter table tablename add column field type constraints;
insert into tablename values(value1, value2...);
update tablename set field1=value1;
select fieldlist from tablename where condition;
delete from tablename where condition;
drop table tablename;
```


Example:

```sql
create table Customer(customerID int unsigned not null primary key,
                    name varchar(20));
create table Payment(paymentID int unsigned not null primary key,
                    customerID int unsigned,
                    payment float,
                    date timestamp,
                    foreign key(customerID) references Customer(customerID));
alter table Customer add column age int;
insert into Customer values(1, "John Doe", 19);
insert into Payment values(1, 1, 4.20, now());
```
Would create:
Customer ([customerID](http://no.com), name, age)
Payment ([paymentID](http://no.com), *customerID*, payment, date)
**NB:** [underlined](http://www.no.com) for primary keys and *italics* for foreign keys


**Joined Query**
For the two tables (Customer and Payment) in the current database, list all customer names and payments record if their age is between 18- 20

```sql
select c.name, p.payment from Customer c, Payment p
where (c.customerID = p.customerID) and (age between 18 and 20);

select c.name, p.payment from Customer c
join Payment p on c.customerID = p.customerID
where age between 18 and 20;
```




