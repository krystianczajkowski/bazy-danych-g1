# Link do [zadań](https://github.com/kropiak/bazy_inf/blob/main/lab_05/lab_05.pdf)
# CICHA WODA
## 1.1 

``` SQL
delete from postac where rodzaj=1 and nazwa <> 'Bjorn' order by data_urodzenia asc limit 2;
-- delete from postac where rodzaj=1 and nazwa != 'Bjorn' order by wiek desc limit 2;
```

## 1.2
``` SQL
alter table przetwory drop foreign key przetwory_ibfk_1;
alter table przetwory drop foreign key przetwory_ibfk_2;
alter table walizka drop foreign key walizka_ibfk_1;
alter table postac modify id_postaci int;
-- alter table postac change id_postaci id_postaci int;
alter table postac drop primary key;
```
# SYRENKA

## 2.1
``` SQL
alter table postac add pesel char(11) first;
update postac set pesel='10000300000' + id_postaci;
alter table postac add primary key(pesel);
```
## 2.2
``` SQL
alter table postac modify rodzaj enum('wiking', 'ptak', 'kobieta', 'syrena');
```
## 2.3
```SQL
insert into postac(id_postaci, pesel, nazwa, rodzaj, data_ur, wiek) values (7, '45698712300', 'Gertruda Nieszczera', 4, '1201-11-22', 78);
```

# PRZECHYŁY
## 3.1
``` SQL
update postac set nazwa_statku = 'Mors' where nazwa like '%a%';
-- update postac set nazwa_statku = 'Mors' where nazwa regexp '[a]';
```

## 3.2
```SQL
update statek set max_ladownosc = max_ladownosc * 0.7 where data_wodowania beetween '1901-01-01' and '2000-11-31';
--                                                          year(data_wodowania) between 1901 and 2000;
```
## 3.3
```SQL
alter table postac add check (wiek <= 1000);
```

# WĄŻ LOKO
## 4.1
``` SQL
alter table postac modify rodzaj enum('wiking', 'ptak', 'kobieta', 'syrena', 'gad');
insert into postac (id_postaci, pesel, nazwa, data_ur, wiek, rodzaj) values (8, '00000000000','Loko', '666-06-06', 611, 5);
```
## 4.2
```SQL
create table marynarz like postac;
insert into marynarz (select * from postac WHERE nazwa_statku is not null);
```
## 4.3
> Przy skorzystaniu z drugiej opcji w [4.2](#42)
```SQL
alter table marynarz add primary key(pesel);
```
# SZTORM
## 5.1
``` SQL
update postac set nazwa_statku = NULL where pesel;
```
## 5.2
``` SQL
delete from postac where rodzaj = 1 and nazwa != 'Bjorn' limit 1;
```
## 5.3
``` SQL
delete from statek where nazwa_statku is not null;
```
## 5.4
``` SQL
drop table statek;
```
## 5.5
``` SQL
create table zwierz (
zwierz_id int primary key auto_increment,
nazwa varchar(55),
wiek int unsigned);
```
## 5.6
``` SQL
insert into zwierz(nazwa, wiek) select nazwa, wiek from postac where rodzaj = 'ptak' or rodzaj = 'gad';
```
> tablesgenerator.com
