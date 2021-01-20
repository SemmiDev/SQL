**`©2021 | sammidev `**
# KAK MEONG | TUGAS 3 | STIE HANG TUAH #

## Database ##

* MySQL

## Software Needs ##

* XAMPP
* IDE (DataGrip/PHPMyAdmin/MySQL Workbench)

## Resources ##

* Question : /resources/tugas-3/TUGAS BASIS DATA 3.pdf
* Data : /resources/tugas-3/Materi latihan 3.csv
* full sql : /resources/tugas-3/jawaban.sql

## Steps ##

1. Create a database
```sql
CREATE DATABASE IF NOT EXISTS mahasiswa_sammialdhiyanto;
SHOW DATABASES;
USE mahasiswa_sammialdhiyanto;
```

2. Create a table
```sql
CREATE TABLE ALUMNI_SammiAldhiYanto (
    NIM VARCHAR(8) DEFAULT NULL,
    TMPT_LAHIR VARCHAR(100) DEFAULT NULL ,
    TGL_LAHIR DATE DEFAULT NULL ,
    PRODI ENUM('SI','TI') DEFAULT NULL,
    EMAIL VARCHAR(100) DEFAULT NULL,
    IPK TEXT DEFAULT NULL ,
    KELAMIN ENUM('PRIA','WANITA') DEFAULT NULL,
    THN_MASUK INT DEFAULT NULL,
    THN_LULU INT DEFAULT NULL,
    JUDUL VARCHAR(100) DEFAULT NULL
);
```

3. Import data

![Screenshot (1192)](https://user-images.githubusercontent.com/55814880/105155165-db479900-5b3c-11eb-9a2b-98a01c211cb3.png)

4. Remove 'title' field
```sql
ALTER TABLE alumni_sammialdhiyanto
    DROP COLUMN JUDUL;
```

5. Added the ID field
```sql
ALTER TABLE alumni_sammialdhiyanto
    ADD COLUMN id INT PRIMARY KEY AUTO_INCREMENT FIRST;
```

6. Aggregate Data

**`Berapa Rata-rata IPK Seluruh Alumni`**
```sql
SELECT AVG(IPK) FROM ALUMNI_SammiAldhiYanto;
```

**`Berapa Rata-rata IPK Bagi Alumni berjenis Kelamin Pria`**
```sql
SELECT AVG(IPK) FROM ALUMNI_SammiAldhiYanto WHERE KELAMIN = 'PRIA';
```

**`Berapa Rata-rata IPK Bagi Alumni berjenis Kelamin Wanita`**
```sql
SELECT AVG(IPK) FROM ALUMNI_SammiAldhiYanto WHERE KELAMIN = 'WANITA';
```

**`Berapa Rata-rata IPK Bagi Alumni Prodi SI`**
```sql
SELECT AVG(IPK) FROM ALUMNI_SammiAldhiYanto WHERE PRODI = 'SI';
```

**`Berapa Rata-rata IPK Bagi Alumni Prodi TI`**
```sql
SELECT AVG(IPK) FROM ALUMNI_SammiAldhiYanto WHERE PRODI = 'TI';
```

**`Berapa Nilai Minimum IPK Alumni Prodi TI yang Berjenis Kelamin Pria`**
```sql
SELECT MIN(IPK) FROM ALUMNI_SammiAldhiYanto WHERE PRODI = 'TI' AND KELAMIN = 'PRIA';
```

**`Berapa Nilai Maksimum IPK Alumni Prodi SI yang Berjenis Kelamin Wanita`**
```sql
SELECT MIN(IPK) FROM ALUMNI_SammiAldhiYanto where PRODI = 'SI' AND KELAMIN = 'WANITA';
```

**`Berapa Jumlah banyaknya Alumni Prodi TI dan Berikan Keterangan (alias) dengan
nama “Total Alumni Prodi TI”`**
```sql
SELECT COUNT(id) AS 'Total Alumni Prodi TI' FROM alumni_sammialdhiyanto;
```

**`Berapa Jumlah banyaknya Alumni Prodi Prodi SI yang kelahiran Pekanbaru dan Berikan
Keterangan (alias) dengan nama “Total Alumni Prodi SI Kelahiran Pekanbaru”
`**
```sql
SELECT COUNT(id) AS 'Total Alumni Prodi SI Kelahiran Pekanbaru' FROM alumni_sammialdhiyanto WHERE PRODI = 'SI' AND TMPT_LAHIR = 'Pekanbaru';
```

**`Berapa Jumlah Banyaknya Seluruh Alumni yang memiliki IPK diatas 3,50`**
```sql
SELECT COUNT(id) AS 'Total alumni yg memiliki ipk diatas 3,50' FROM alumni_sammialdhiyanto WHERE IPK > '3,50';
```
