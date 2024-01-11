# Link do [zadań](https://github.com/kropiak/zti_bazy/blob/master/lab_3/lab_3_zadania_1.md)
# Funkcje, agregacja i grupowanie.

## 1
```SQL
select imie, nazwisko, data_urodzenia from pracownik;
```

## 2
```SQL
select imie, nazwisko, year(now())-year(data_urodzenia) as wiek
from pracownik;
```

## 3
```SQL
select nazwa, count(*) from dzial d, pracownik p
where d.id_dzialu=p.dzial
group by nazwa;
```

## 4
```SQL
```

## 5
```SQL
```

## 6
```SQL
select round(avg(pensja), 2) from pracownik;
```

## 7
```SQL
select round(avg(pensja), 2) from pracownik where data_zatrudnienia < subdate(data_zatrudnienia, interval 5 year);
```

## 8
```SQL
liczenie ogolnych zamowien
select t.nazwa_towaru, p.towar, sum(p.ilosc) as suma
from towar t
join pozycja_zamowienia p on t.id_towaru=p.towar
group by p.towar
order by suma desc
limit 10;

-- liczenie ilosci unikalnych zamowien
select t.nazwa_towaru, p.towar, count(*) suma
from towar t
join pozycja_zamowienia p on t.id_towaru=p.towar
group by p.towar
order by suma desc
limit 10;
```

## 9
```SQL
select z.numer_zamowienia, sum(p.ilosc*p.cena), z.id_zamowienia
from zamowienie z
join pozycja_zamowienia p on z.id_zamowienia=p.zamowienie
where year(z.data_zamowienia)=2017
and quarter(z.data_zamowienia) = 1
group by z.id_zamowienia;
```

## 10
```SQL
select pr.imie, pr.nazwisko, sum(p.ilosc*p.cena) suma
from zamowienie z
join pozycja_zamowienia p on z.id_zamowienia=p.zamowienie
join pracownik pr on pr.id_pracownika=z.pracownik_id_pracownika
group by pr.id_pracownika
order by suma desc;
```
