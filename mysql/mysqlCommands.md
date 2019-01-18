mysql -u root -p

show databases;

use purchases;

show tables;

show columns from groceries;

rename table groceries to tblGroceries;

alter table groceries add column price float;

alter table groceries modify column datum date after id;

insert into groceries (datum,location,store,item,price) values ('2019-01-12','Downers Grove',"Jewel Osco",'Yoghurt noosa',1.48);

select * from groceries;

select * from groceries where item = 'Apple';

select * from groceries where item like 'Yoghurt%';

select * from groceries where price > 10;

create table tblStores
(store_id int auto_increment primary key,
store varchar(20),
street varchar(50),
city varchar(20),
zip int);

select * from tblGroceries, tblStores where tblGroceries.store_id=tblStores.store_id;