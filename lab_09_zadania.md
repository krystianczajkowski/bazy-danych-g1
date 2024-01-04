# Link do [zadań](https://github.com/kropiak/bazy_inf/blob/main/lab_09/lab_09.pdf)

# DZIURA
## 1.1
```SQL
delimiter //
create trigger kreatura_before_insert before insert on kreatura
  for each row
  begin
    if new.waga > 0 then
      signal sqlstate '45000' set message_text = 'waga mniejsza od 0';
    end if;
  end//

delimiter //
create trigger kreatura_before_update before update on kreatura
  for each row
  begin
    if new.waga > 0 then
      signal sqlstate '45000' set message_text = 'waga mniejsza od 0';
    end if;
  end//
```

# FUTRO

## 2.1
```SQL
create table archiwum_wypraw(

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

