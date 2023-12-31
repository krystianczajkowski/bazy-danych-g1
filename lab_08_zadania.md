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

select distinct(nazwa) from kreatura k
right outer join uczestnicy u on k.idKreatury=u.id_uczestnika;
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
select w.nazwa, count(u.id_uczestnika) as liczba_uczestnikow,
       group_concat(k.nazwa separator ' - ') as uczestnicy
from wyprawa w join uczestnicy u on
w.id_wyprawy=u.id_wyprawy
join kreatura k on k.idKreatury=u.id_uczestnika
group by w.nazwa;
```

## 2.2
```SQL
select k.nazwa, w.nazwa,
       s.nazwa as nazwa_sektora, e.idEtapu, w.data_rozpoczecia
from etapy_wyprawy e
join sektor s on e.sektor=s.id_sektora
join wyprawa w on e.idWyprawy=w.id_wyprawy
join kreatura k on w.kierownik=k.idKreatury
order by w.data_rozpoczecia, e.kolejnosc;
```

# MISTERNY PLAN

## 3.1
```SQL
select nazwa as nazwa_sektora, 0 as liczba_odwiedzin
from sektor
where id_sektora not in (select distinct(s.id_sektora)
                         from sektor s, etapy_wyprawy e
                         where s.id_sektora=e.sektor)
union
select distinct(s.nazwa) as nazwa_sektora,
       count(s.id_sektora) as liczba_odwiedzin
from etapy_wyprawy e
join sektor s on e.sektor=s.id_sektora
group by nazwa_sektora;

select s.nazwa, ifnull(count(ew.sektor), 0) as liczba_odwiedzin
from sektor s
left join etapy_wyprawy ew on s.id_sektora=ew.sektor
group by s.nazwa;
```

## 3.2
```SQL
select k.nazwa, if(count(u.id_uczestnika) > 0,
                "bral udzial", "nie bral") as udzial
from kreatura k
left join uczestnicy u on k.idKreatury=u.id_uczestnika
group by k.nazwa;
```

# PUŁAPKA

## 4.1
```SQL
select w.nazwa, sum(length(ew.dziennik)) as liczba_znakow
from wyprawa w
join etapy_wyprawy ew on w.id_wyprawy=ew.idWyprawy
group by w.nazwa
having liczba_znakow < 400;
```

## 4.2
```SQL
select w.nazwa as nazwa_wyprawy,
       sum(z.waga*e.ilosc)/count(distinct(u.id_uczestnika)) as niesione_rzeczy
from ekwipunek e
join uczestnicy u on e.idKreatury=u.id_uczestnika
join wyprawa w on u.id_wyprawy=w.id_wyprawy
join zasob z on z.idZasobu=e.idZasobu
group by w.nazwa;
```

# TCHÓRZ

## 5.1
```SQL
select k.nazwa, datediff(w.data_rozpoczecia, k.dataUr) as wiek
from sektor s
join etapy_wyprawy ew on s.id_sektora=ew.sektor
join wyprawa w on w.id_wyprawy = ew.idWyprawy
join uczestnicy u on w.id_wyprawy=u.id_wyprawy
join kreatura k on k.idKreatury=u.id_uczestnika
where s.nazwa = 'Chatka Dziadka';
```
