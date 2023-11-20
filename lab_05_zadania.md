# Link do [zadań](https://github.com/kropiak/bazy_inf/blob/main/lab_05/lab_05.pdf)
# CICHA WODA
## 1.1 

``` SQL
delete from postac where rodzaj=1 and nazwa <> 'Bjorn' order by data_urodzenia asc limit 2;
```

## 1.2
``` SQL
alter table przetwory drop foreign key przetwory_ibfk_1;
alter table przetwory drop foreign key przetwory_ibfk_2;
alter table postac drop foreign key postac_ibfk_1;
alter table walizka drop foreign key walizka_ibfk_1;
alter table postac modify id_postaci int;
alter table postac drop primary key;
```
# SYRENKA

## 2.1
``` SQL
alter table postac add pesel(char(11) primary key);
```
## 2.2
``` SQL
alter table postac modify rodzaj ('wiking', 'ptak', 'kobieta', 'syrena');
```
## 2.3
```SQL
inseret into postac ('Gertruda Nieszczera',
```

# PRZECHYŁY
## 3.1
``` SQL
```

## 3.2
```SQL
```
## 3.3

# WĄŻ LOKO
## 4.1
``` SQL
```
## 4.2
```SQL
```
## 4.3 
```SQL
```
# SZTORM
## 5.1
``` SQL
```
## 5.2
``` SQL
```
## 5.3
``` SQL
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
wiek int unsigned
```
## 5.6
``` SQL
```
