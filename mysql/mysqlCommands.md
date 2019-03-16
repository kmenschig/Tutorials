mysql -u root -p

show databases;

use purchases;

show tables;

show columns from groceries;

rename table groceries to tblGroceries;

alter table groceries add column price float;

alter table groceries modify column datum date after id;

alter table tblDocuments change StatusChangedOn StatusChanged_Text varchar(50);

insert into groceries (datum,location,store,item,price) values ('2019-01-12','Downers Grove',"Jewel Osco",'Yoghurt noosa',1.48);

select * from groceries;

select * from groceries where item = 'Apple';

select * from tblGroceries where item like 'Salad%';

select * from groceries where item like 'Yoghurt%';

select * from groceries where price > 10;

select purchase_date, sum(price) as total_cost from tblGroceries where store_id=1 group by purchase_date;

select store_id, sum(price) as total_cost from tblGroceries where date_format(purchase_date,'%Y%m') =  
date_format(subdate(curdate(),interval 1 month), '%Y%m') group by store_id;

select year(purchase_date), month(purchase_date), sum(price) from tblGroceries group by year(purchase_date), month(purchase_date);

select * from tblGroceries order by purchase_date desc;

create table tblStores
(store_id int auto_increment primary key,
store varchar(20),
street varchar(50),
city varchar(20),
zip int);

select * from tblGroceries, tblStores where tblGroceries.store_id=tblStores.store_id;

update tblGroceries
set item='Coffee Creamer 64 oz'
where id=25;

update tblDocuments set InitiationDate= str_to_date(Initiation_Text, '%m/%d/%Y') where Initiation_Text<>"";

update tblDocuments set InitiationDate= str_to_date(Initiation_Text, '%m/%d/%Y') where Initiation_Text<>"";

update tblDocuments set Completion_Text= replace(Completion_Text, ' 0:00:00', "")
where Completion_Text<>"";

select * from tblDocuments\G;

pager less -SFX;    #to show a huge table organized in columns