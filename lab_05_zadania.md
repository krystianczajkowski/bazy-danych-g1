# Link do [zadań](https://github.com/kropiak/bazy_inf/blob/main/lab_05/lab_05.pdf)
# CICHA WODA
## 1.1 

``` SQL
DELTE FROM postac WHERE wiek = (SELECT MAX(wiek) FROM postac WHERE rodzaj =1) AND id_postaci != 1;
DELTE FROM postac WHERE wiek = (SELECT MAX(wiek) FROM postac WHERE rodzaj =1) AND id_postaci != 1;
```
## 1.2

