# Link do [zadań](https://github.com/kropiak/bazy_inf/blob/main/lab_09/lab_09.pdf)

# DZIURA
## 1.1
```SQL
delimiter //
create trigger kreatura_before_insert before insert on kreatura
  for each row
  begin
    if new.waga < 0 then
      signal sqlstate '45000' set message_text = 'waga mniejsza od 0';
    end if;
  end//
delimiter ;

delimiter //
create trigger kreatura_before_update before update on kreatura
  for each row
  begin
    if new.waga < 0 then
      signal sqlstate '45000' set message_text = 'waga mniejsza od 0';
    end if;
  end//
delimiter ;

delimiter //
create trigger kratura_before_insert before insert on kreatura
  for each row
  begin
    if new.waga < 0 then
      set new.waga = 1;
    end if;
  end//
delimiter ;
```

# FUTRO

## 2.1
```SQL
create table archiwum_wypraw(
id_wyprawy int primary key auto_increment,
nazwa varchar(55),
data_rozpoczecia date,
data_zakonczenia date,
kierownik varchar(55));

delimiter //
create trigger wyprawa_before_delete before delete on wyprawa
  for each row
  begin
    insert into archiwum_wypraw
    select w.id_wyprawy, w.nazwa, w.data_rozpoczecia, w.data_zakonczenia, k.nazwa
    from wyprawa w join kreatura k on k.idKreatury=w.kierownik
    where id_wyprawy=old.id_wyprawy;
  end//
delimiter ;
```

# SPALONY

## 3.1
```SQL
delimiter //
create procedure eliksir_sily (in id int)
  begin
    update kreatura set udzwig = udzwig * 1.2 where idKreatury = id;
  end//
delimiter ;
```

## 3.2
```SQL
create function wielkie_litery (t text)
  returns text
  return upper(t);
```

# SALWA ŚMIECHU

## 4.1
```SQL
create table system_alarmowy(
id_alarmu int primary key auto_increment,
wiadomosc text);
```

## 4.2
```SQL
select idKreatury from kreatura where nazwa = 'Tesciowa' into @tesciowa;
select id_sektora from sektor where nazwa = 'Chatka Dziadka' into @dziad;
declare czy_tesc bool;
declare czy_dzial bool;

delimiter //
create trigger system_alarmowy_after_insert after insert on uczestnicy
  for each row
  begin
    if @tesciowa in
      (select id_uczestnika from uczestnicy where id_wyprawy=new.id_wyprawy)
    then
      set czy_tesc = true;
    end if;
    if @dziad in
      (select sektor from etapy_wyprawy where id_wyprawy=new.id_wyprawy)
    then
      set czy_dziad = true
    end if;

    if czy_tesc and czy_dziad then
      insert into system_alarmowy values(default, 'Tesciowa nadchodzi !!!', default);
    end if;
  end//
delimiter ;
```

# HAPPY END

## 5.1
```SQL
delimiter //
-- SSMUiK średnia, suma, max udźwig i kreatury
create procedure ssmuik(out avg float, out suma int, out max_load int )
  begin
    select sum(udzwig)/count(*) as avg, sum(udzwig) as suma, max(udzwig) as max_load from kreatura;
  end//
delimiter ;
```

## 5.2
```SQL
create procedure wyprawa_sektory(in id_wyprawy int, out numer_sektora int)
  begin
  end;
```

