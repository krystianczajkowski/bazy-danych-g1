# Link do [zadań](https://github.com/kropiak/bazy_inf/blob/main/lab_07/lab_07.pdf)

# SKWAREK

## 1.1
```SQL
select round(avg(waga), 2) as srednia_waga
from kreatura where rodzaj = 'wiking';
```

## 1.2
```SQL
select round(avg(waga), 2) as srednia_waga, rodzaj,
       count(rodzaj) as ilosc
from kreatura group by rodzaj;

-- do policzenia rodzaju gdzie wartość to NULL
select round(avg(waga), 2) as srednia_waga,
       rodzaj, count(*) as ilosc
from kreatura group by rodzaj;
```

## 1.3
```SQL
select round(avg(year(dataUr)),2) as sredni_wiek, rodzaj
from kreatura group by rodzaj;
```

# DYMEK

## 2.1
```SQL
select sum(waga*ilosc) as suma_wag, rodzaj from zasob group by rodzaj;
```

## 2.2
```SQL
select nazwa, round(avg(waga*ilosc), 2) as srednia_waga
from zasob where ilosc >= 4
group by nazwa
having srednia_waga > 10;
```

## 2.3
```SQL
select rodzaj, count(distinct(nazwa)) as nazwa
from zasob
group by rodzaj
having min(ilosc) > 1;
```

# PIEPRZ

## 3.1
```SQL
select k.nazwa, sum(e.ilosc) as niesione_rzeczy
from kreatura k, ekwipunek e
where k.idKreatury = e.idKreatury
group by k.nazwa;
```

## 3.2
```SQL
select k.nazwa, z.nazwa from kreatura k
join ekwipunek e on k.idKreatury=e.idKreatury
join zasob z on e.idZasobu=z.idZasobu;
```

## 3.3
```SQL
select * from kreatura k left join ekwipunek e on k.idKreatury = e.idKreatury where e.idKreatury is NULL;
select * from kreatura where idKreatury not in (select distinct idKreatury from ekwipunek where idKreatury is not null);
```

# DZIADEK

## 4.1
```SQL
select k.dataUr, k.nazwa, z.nazwa from kreatura k
join ekwipunek e on k.idKreatury=e.idKreatury
join zasob z on e.idZasobu=z.idZasobu
where year(k.dataUr) between 1670 and 1679
and k.rodzaj = 'wiking';
```

## 4.2
```SQL
select k.nazwa, k.dataUr as dU, z.nazwa
from kreatura k
join ekwipunek e on k.idKreatury = e.idKreatury
join zasob z on e.idZasobu = z.idZasobu
where z.rodzaj = 'jedzenie'
order by dU limit 5;
```

## 4.3
```SQL
select k1.nazwa, k2.nazwa
from kreatura k1, kreatura k2 where k1.idKreatury = k2.idKreatury + 5;

select k2.idKreatury, concat(k2.nazwa, ' - ' ,k1.nazwa) as nazwa, k1.idKreatury
from kreatura k1 join kreatura k2 on k1.idKreatury = k2.idKreatury + 5;
```

# ZŁA NOWINA

## 5.1
```SQL
```

## 5.2
```SQL
```
