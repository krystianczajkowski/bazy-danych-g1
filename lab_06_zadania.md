# link  do [zadań](https://github.com/kropiak/bazy_inf/blob/main/lab_06/lab_06.pdf)
# ROZBITEK
## 1.1
```SQL
create table kretura like wikingowie.kreatura;
create table zasob like wikingowie.zasob;
create table ekwipunek like wikingowie.ekwipunek;
```
## 1.2
```SQL
select * from zasob;
```

## 1.3
```SQL
select * from zasob where rodzaj = 'jedzenie';
```

## 1.4
```SQL
select z.idZasobu, z.nazwa, z.waga, z.ilosc, z.dataPozyskania, z.rodzaj
from zasob z join ekwipunek e on z.idZasobu=e.idZasobu
join kreatura k on e.idKreatury=k.idKreatury
where k.idKreatury in (1, 3, 5);
```
# KOKOS?
## 2.1
```SQL
select kreatura.nazwa, kreatura.rodzaj, sum(zasob.waga * zasob.ilosc) as n from kreatura join ekwipunek on kreatura.idKreatury=ekwipunek.idKreatury join zasob on ekwipunek.idZasobu=zasob.idZasobu where kreatura.rodzaj != 'wiedzma' grou
p by kreatura.nazwa having n > 50;

```

## 2.2
```SQL
select nazwa, waga from zasob where waga between 2 and 5;
```
## 2.3
```SQL
select kreatura.nazwa, kreatura.rodzaj from kreatura join ekwipunek on kreatura.idKreatury=ekwipunek.idKreatury join zasob on ekwipunek.idZasobu=zasob.idZasobu where kreatura.nazwa like '%or%'
group by kreatura.nazwa having sum(zasob.waga * zasob.ilosc) between 30 and 70;
```
# HAMAK

## 3.1
```SQL
```
## 3.2
```SQL
```
## 3.3
```SQL
```
# ZŁOTA RYBKA
## 4.1
```SQL
```
## 4.2
```SQL
```
## 4.3
```SQL
```

# TWARDY SEN
## 5.1
```SQL
```
## 5.2
```SQL
```
## 5.3
```SQL
```
