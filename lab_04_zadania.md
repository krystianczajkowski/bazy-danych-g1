# LIST
## 1.1
``` SQL
CREATE TABLE `postac` (
  `id_postaci` int NOT NULL AUTO_INCREMENT,
  `nazwa` varchar(40) DEFAULT NULL,
  `rodzaj` enum('wiking','ptak','kobieta') DEFAULT NULL,
  `data_ur` date DEFAULT NULL,
  `wiek` int unsigned DEFAULT NULL,
  PRIMARY KEY (`id_postaci`);
```
## 1.2
``` SQL
INSERT INTO postac(nazwa, rodzaj, data_ur, wiek) VALUES('Bjorn', 1, '1254-11-09', 22);
INSERT INTO postac(nazwa, rodzaj, data_ur, wiek) VALUES('Drozd', 2, '1274-11-09', 2);
INSERT INTO postac(nazwa, rodzaj, data_ur, wiek) VALUES('Tesciowa', 1, '1234-11-09', 62);
```
## 1.3
``` SQL
UPDATE postac SET wiek=88 WHERE nazwa='Tesciowa';
```

# PANIKA
## 2.1
``` SQL
CREATE TABLE walizka(
id_walizki INT PRIMARY KEY AUTO_INCREMENT,
pojemnosc INT UNSIGNED,
kolor ENUM('rozowy', 'czerwony', 'teczowy', 'zolty'),
id_wlasciciela INT NOT NULL,
FOREIGN KEY(id_wlasciciela) REFERENCES postac(id_postaci) ON DELETE CASCADE
);
```

## 2.2
``` SQL
 ALTER TABLE walizka MODIFY COLUMN kolor ENUM('rozowy', 'czerwony', 'teczowy', 'zolty') DEFAULT 'rozowy';
```

*albo*

``` SQL
ALTER TABLE walizka ALTER kolor SET DEFAULT 'rozowy';
```

## 2.3 
``` SQL
INSERT INTO walizka(pojemnosc, kolor, id_wlasciciela) VALUES(120, 2, 1);
INSERT INTO walizka(pojemnosc, id_wlasciciela) VALUES(240, 3);
```

# NIESPODZIANKA
## 3.1
``` SQL
CREATE TABLE izba(
adres_budynku VARCHAR(100),
nazwa_izby VARCHAR(100),
metraz INT UNSIGNED,
wlasciciel INT,
PRIMARY KEY(adres_budynku, nazwa_izby),
FOREIGN KEY(wlasciciel) REFERENCES postac(id_postaci) ON DELETE SET NULL);
```
## 3.2
``` SQL
ALTER TABLE izba ADD COLUMN kolor_izby VARCHAR(45) DEFAULT 'czarny' AFTER metraz;
```
## 3.3
```SQL
INSERT INTO izba(adres_budynku, nazwa_izby, metraz, wlasciciel) VALUES ('ul. Reymonta 13/3', 'spizarnia', 10, 1);
```

# KOSZMAR
## 4.1
``` SQL
CREATE TABLE przetwory(
id_przetworu INT PRIMARY KEY AUTO_INCREMENT,
rok_produkcji SMALLINT DEFAULT 1654,
zawartosc VARCHAR(255),
dodatek VARCHAR(255) DEFAULT 'papryczka chilli',
id_wykonawcy INT,
id_konsumenta INT,
FOREIGN KEY(id_wykonawcy) REFERENCES postac(id_postaci),
FOREIGN KEY(id_konsumenta) REFERENCES postac(id_postaci)
);
```
## 4.2
``` SQL
INSERT INTO przetwory(id_wykonawcy, zawartosc, id_konsumenta) VALUES (1, 'Bigos', 3);
```

# UCIECZKA
## 5.1
``` SQL
INSERT INTO postac(nazwa, rodzaj, data_ur, wiek) VALUES('Birger', 1, '1255-11-08', 18);
INSERT INTO postac(nazwa, rodzaj, data_ur, wiek) VALUES('Bo', 1, '1254-11-08', 19);
INSERT INTO postac(nazwa, rodzaj, data_ur, wiek) VALUES('Erik', 1, '1256-11-08', 17);
INSERT INTO postac(nazwa, rodzaj, data_ur, wiek) VALUES('Gorm', 1, '1253-11-08', 20);
INSERT INTO postac(nazwa, rodzaj, data_ur, wiek) VALUES('Halfdan', 1, '1252-11-08', 21);
```
## 5.2
``` SQL
CREATE TABLE statek(
nazwa_statku VARCHAR(255) PRIMARY KEY,
rodzaj_statku ENUM('barka', 'pchacz', 'prom', 'roporudomasowiec', 'frachtowiec', 'tramwaj wodny', 'uzbrojony statek handlowy'),
data_wodowania DATE,
max_ladownosc INT UNSIGNED);
```
## 5.3
``` SQL
INSERT INTO statek(nazwa_statku, rodzaj_statku, data_wodowania, max_ladownosc) VALUES ('Mors', 1, '1234-11-08', 12000);
INSERT INTO statek(nazwa_statku, rodzaj_statku, data_wodowania, max_ladownosc) VALUES ('Mors-2', 1, '1234-11-09', 24000);
```
## 5.4
``` SQL
ALTER TABLE postac ADD COLUMN funkcja VARCHAR(45);
```
## 5.5
``` SQL
UPDATE postac SET funkcja='kapitan' WHERE id_postaci=1;
```
## 5.6
``` SQL
ALTER TABLE postac ADD COLUMN nazwa_statku VARCHAR(255);
ALTER TABLE postac ADD CONSTRAINT FOREIGN KEY(nazwa_statku) REFERENCES statek(nazwa_statku);
```
## 5.7
```SQL
UPDATE postac SET nazwa_statku='Mors' WHERE rodzaj in (1,2);
```

## 5.8
``` SQL
DELETE FROM izba WHERE nazwa_izby='spizarnia';
```

## 5.9
```SQL
DROP TABLE izba;
```  


