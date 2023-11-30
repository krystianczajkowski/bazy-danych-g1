# Link  do [zadań](https://github.com/kropiak/bazy_inf/blob/main/lab_06/lab_06.pdf)
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
select z.idZasobu, z.ilosc
from zasob z join ekwipunek e on z.idZasobu=e.idZasobu
join kreatura k on e.idKreatury=k.idKreatury
where k.idKreatury in (1, 3, 5);
```
# KOKOS?
## 2.1
```SQL
select kreatura.nazwa, kreatura.rodzaj
from kreatura
join ekwipunek on kreatura.idKreatury=ekwipunek.idKreatury
join zasob on ekwipunek.idZasobu=zasob.idZasobu
where kreatura.rodzaj != 'wiedzma'
group by kreatura.idKreatury
having sum(zasob.waga * ekwipunek.ilosc) > 50;
```

## 2.2
```SQL
select nazwa, waga from zasob
where waga between 2 and 5;
```
## 2.3
```SQL
select kreatura.nazwa, kreatura.rodzaj
from kreatura
join ekwipunek on kreatura.idKreatury=ekwipunek.idKreatury
join zasob on ekwipunek.idZasobu=zasob.idZasobu
where kreatura.nazwa like '%or%'
group by kreatura.idKreatury
having sum(zasob.waga * ekwipunek.ilosc) > 30
and sum(zasob.waga * ekwipunek.ilosc) < 70;
```
# HAMAK

## 3.1
```SQL
select * from zasob
where month(dataPozyskania) in (7, 8);
```
## 3.2
```SQL
select * from zasob
where rodzaj is not null
order by waga;
```
## 3.3
```SQL
select * from kreatura
where dataUr is not null
order by dataUr limit 5;
```
# ZŁOTA RYBKA
## 4.1
```SQL
select disitnct rodzaj from zasob;
```
## 4.2
```SQL
select concat(nazwa, ' - ', rodzaj) as 'nazwa - rodzaj'
from kreatura where rodzaj like 'wi%';
```
## 4.3
```SQL
select nazwa, (ilosc*waga) as calkowitaWaga
from zasob where year(dataPozyskania) between 2000 and 2007;
```

# TWARDY SEN
## 5.1
```SQL
select waga*ilosc as calaWaga,
       ilosc*waga * 0.7 as jedzenieWlasciwe,
       ilosc*waga * 0.3 as wagaOdpadow
from zasob where rodzaj = 'jedzenie';
```
## 5.2
```SQL
select * from zasob where rodzaj is null;
```
## 5.3
```SQL
select rodzaj
from zasob
where nazwa like 'Ba%'
or nazwa like '%or'
order by rodzaj;
```
