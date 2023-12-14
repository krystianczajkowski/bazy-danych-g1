# Link do [zadań](https://github.com/kropiak/bazy_inf/blob/main/lab_08/lab_08.pdf)

# SPISEK

## 1.1
```SQL
create table kreatura like wikingowie.kreatura;
insert into kreatura (select * from wikingowie.kreatura);

create table uczestnicy like wikingowie.uczestnicy;
insert into uczestnicy select * from wikingowie.uczestnicy;

create table etapy_wyprawy like wikingowie.etapy_wyprawy;
insert into etapy_wyprawy select * from wikingowie.etapy_wyprawy;

create table sektor like wikingowie.sektor;
insert into sektor select * from wikingowie.sektor;

create table wyprawa like wikingowie.wyprawa;
insert into wyprawa select * from wikingowie.wyprawa;
```

## 1.2
```SQL
select nazwa from kreatura
where idKreatury not in (select distinct k.idKreatury
                        from kreatura k, uczestnicy u
                        where k.idKreatury=u.id_uczestnika);
```

## 1.3
```SQL
select w.nazwa as nazwa_wyprawy, sum(e.ilosc) as niesione_rzeczy
from kreatura k
join ekwipunek e on k.idKreatury=e.idKreatury
join uczestnicy u on k.idKreatury=u.id_uczestnika
join wyprawa w on u.id_wyprawy=w.id_wyprawy
group by w.nazwa;
```

# TRUDNA DECYZJA

## 2.1
```SQL

```

## 2.2
```SQL
```

# MISTERNY PLAN

## 3.1
```SQL
```

## 3.2
```SQL
```

# PUŁAPKA

## 4.1
```SQL
```

## 4.2
```SQL
```

# TCHÓRZ

## 5.1
```SQL
```
