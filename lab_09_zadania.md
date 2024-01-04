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

create trigger kreatura_before_update before update on kreatura
  for each row
  begin
    if new.waga < 0 then
      signal sqlstate '45000' set message_text = 'waga mniejsza od 0';
    end if;
  end//

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
```

## 3.2
```SQL
```

# SALWA ŚMIECHU

## 4.1
```SQL
```

## 4.1
```SQL
```

# HAPPY END

## 5.1
```SQL
```

## 5.2
```SQL
```

