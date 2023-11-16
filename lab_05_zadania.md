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
