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

