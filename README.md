[See assignment in Alexa](https://alexa.bitmaker.co/cohorts/72/assignments/2247/latest)

#How many dinosaurs we have

dinosaurs=# select count(id) from dinos;
 count
-------
   331
(1 row)

#Find all the dinosaurs from the Jurassic period
dinosaurs=# select * from dinos where period = 'Jurassic';

#Find the total sum length of all the dinosaurs from Cretaceous period.
dinosaurs=# select sum(length) from dinos where period = 'Cretaceous';
   sum   
---------
 1366.45
(1 row)

#Find all the dinosaurs from either the Jurassic or Cretaceous periods and order them by their species name alphabetically.
dinosaurs=# select * from dinos where period ='Jurassic' or period = 'Cretaceous' order by species asc;

#Find all the dinosaurs from the t_order Saurischia that are Herbivorous.
dinosaurs=# select * from dinos where diet='Herbivorous' and t_order = 'Saurischia';

#Find the shortest dinosaur, and rename it Shortie.
dinosaurs=# select min(length) from dinos;

 min  
------
 0.08
(1 row)

dinosaurs=# select name from dinos where length = 0.08;
    name     
-------------
 Liaoxiornis
(1 row)

dinosaurs=# select name from dinos where length =(select min(length) from dinos);
    name     
-------------
 Liaoxiornis
(1 row)

dinosaurs=# update dinos set name = 'Shortie' where name = (select name from dinos where length =(select min(length) from dinos));

UPDATE 1
dinosaurs=# select name from dinos where length =(select min(length) from dinos);                     
name   
---------
 Shortie
(1 row)

#Find the alphabetically first dinosaur.
dinosaurs=# select name from dinos order by name limit(1);
   name   
----------
 Aardonyx
(1 row)

#Rename the five longest dinosaurs The Famous Five.
dinosaurs=# select name from dinos order by length desc limit(5);
      name       
-----------------
 Udanoceratops
 Yingshanosaurus
 Tsagantegia
 Shamosaurus
 Tanius
(5 rows)


update dinos set name = "The Famous Five" where length = (selec


select name, length from dinos where length IS NOT NULL;

select name, length from dinos order by length desc where IS NOT NULL;



select name, length from dinos order by length desc;

update dinos set name = (select name from dinos order by length desc limit(5))



dinosaurs=# select length from (select length from dinos where length is not null) as foo order by length desc;

dinosaurs=# select length from (select length from dinos where length is not null) as foo order by length desc limit(5);



UPDATE dinos set name = 'The Famous Five' WHERE name in (select length from (select length from dinos where length is not null) as foo order by length desc limit(5));
