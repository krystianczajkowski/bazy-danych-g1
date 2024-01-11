# Link do [zadań](https://github.com/kropiak/zti_bazy/blob/master/lab_3/lab_3_zadania_2.md)

# Funkcje, agregacja i grupowanie.

## 1
```SQL
select d.nazwa, max(p.pensja) as maksymalna_pensja, avg(pensja)
from dzial d join pracownik p on d.id_dzialu=p.dzial
group by d.nazwa;
```

## 2
```SQL
select k.pelna_nazwa, (p.ilosc*p.cena) as wartosc_zamowienia from klient k
join zamowienie z on k.id_klienta=z.klient
join pozycja_zamowienia p on z.id_zamowienia=p.zamowienie
order by wartosc_zamowienia desc limit 10;
```

## 3
```SQL
```

## 4
```SQL
select sum(ilosc*cena) as anulowane_zamowienia from pozycja_zamowienia p, zamowienie z
where p.zamowienie=z.id_zamowienia and z.status_zamowienia=6;
```

## 5
```SQL
select count(
```

## 6
```SQL
select 
```

## 7
```SQL
```

## 8
```SQL
select ilosc
```

## 9
```SQL
```

## 10
```SQL
```
