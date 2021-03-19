**`© 2021 | sammidev `**

# Table of Contents

1. [**`Tugas 3`**](#section-1)
2. [**`UAS DATABASE`**](#section-2)
3. [**`Pratikum 2`**](#pratikum-2)
4. [**`Pratikum 3`**](#pratikum-3)
___

### Section 1
# Kak Meianly Salsa Anggraini | Tugas 3 | Hang Tuah #

## Database #

* MySQL

## Software Needs ##

* XAMPP / MYSQL Community Server
* IDE : DataGrip / PHPMyAdmin / MySQL Workbench
* Which i use : *XAMPP & DataGrip*

## Resources ##

* Question : [TUGAS BASIS DATA 3.pdf](https://github.com/SemmiDev/SQL/blob/master/resources/tugas-3/TUGAS%20BASIS%20DATA%203.pdf)
* Data : [Materi latihan 3.csv](https://github.com/SemmiDev/SQL/blob/master/resources/tugas-3/Materi%20Latihan%203.csv)
* full sql : [jawaban.sql](https://github.com/SemmiDev/SQL/blob/master/resources/tugas-3/jawaban.sql)

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
SELECT AVG(replace(IPK,',','.')) FROM ALUMNI_SammiAldhiYanto;
```

**`Berapa Rata-rata IPK Bagi Alumni berjenis Kelamin Pria`**
```sql
SELECT AVG(replace(IPK,',','.')) FROM ALUMNI_SammiAldhiYanto WHERE KELAMIN = 'PRIA';
```

**`Berapa Rata-rata IPK Bagi Alumni berjenis Kelamin Wanita`**
```sql
SELECT AVG(replace(IPK,',','.')) FROM ALUMNI_SammiAldhiYanto WHERE KELAMIN = 'WANITA';
```

**`Berapa Rata-rata IPK Bagi Alumni Prodi SI`**
```sql
SELECT AVG(replace(IPK,',','.')) FROM ALUMNI_SammiAldhiYanto WHERE PRODI = 'SI';
```

**`Berapa Rata-rata IPK Bagi Alumni Prodi TI`**
```sql
SELECT AVG(replace(IPK,',','.')) FROM ALUMNI_SammiAldhiYanto WHERE PRODI = 'TI';
```

**`Berapa Nilai Minimum IPK Alumni Prodi TI yang Berjenis Kelamin Pria`**
```sql
SELECT MIN(replace(IPK,',','.')) FROM ALUMNI_SammiAldhiYanto WHERE PRODI = 'TI' AND KELAMIN = 'PRIA';
```

**`Berapa Nilai Maksimum IPK Alumni Prodi SI yang Berjenis Kelamin Wanita`**
```sql
SELECT MIN(replace(IPK,',','.')) FROM ALUMNI_SammiAldhiYanto where PRODI = 'SI' AND KELAMIN = 'WANITA';
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
SELECT COUNT(id) AS 'Total alumni yg memiliki ipk diatas 3,50' FROM alumni_sammialdhiyanto WHERE replace(IPK,',','.') > '3.50';
```


**`© 2021 | sammidev `**

### Section 2
# Kak Meianly Salsa Anggraini | UAS BASIS DATA | Hang Tuah #

## Database ##

* MySQL

## Software Needs ##

* XAMPP / MYSQL Community Server
* IDE : DataGrip / PHPMyAdmin / MySQL Workbench
* Which i use : *XAMPP & DataGrip*

## Resources ##



* Question : [UAS BASIS DATA.pdf](https://github.com/SemmiDev/SQL/blob/master/resources/uas/UAS%20BASIS%20DATA.pdf)
* Data : [LAMPIRAN DATA UAS.csv](https://github.com/SemmiDev/SQL/blob/master/resources/uas/LAMPIRAN%20DATA%20UAS.csv)

## Steps ##

```sql

# TAMPILKAN SEMUA DATABASES
SHOW DATABASES;

# MEMBUAT DATABASE
CREATE DATABASE PENDIDIKAN_SammiAldhiYanto;

# GUNAKAN DATABASE YG TELAH DIBIKIN
USE PENDIDIKAN_SammiAldhiYanto;

# BIKIN TABLE YANG MASING-MASING COLUMN SESUAI DENGAN DATASET
CREATE TABLE SEKOLAH_SammiALdhiYanto (
    provinsi VARCHAR(50) DEFAULT NULL,
    tingkat_pendidikan ENUM('SD','SMP','SMA','SMK','SLB') DEFAULT NULL,
    jenis_kelamin ENUM('Perempuan','Laki-laki') DEFAULT NULL,
    jumlah_siswa INT UNSIGNED DEFAULT NULL,
    jumlah_guru INT UNSIGNED DEFAULT NULL
);

# SKIP AJA XIXIXI
DESC SEKOLAH_SammiALdhiYanto;

# IMPORT DATA DARI CSV (CURRENTLY : DATAGRIP)

# LIHAT SEMUA DATA YANG TELAH DI IMPORT
SELECT * FROM SEKOLAH_SammiALdhiYanto;

# HAPIUS COLUMN JUMLAH_GURU
ALTER TABLE SEKOLAH_SammiALdhiYanto
    DROP COLUMN jumlah_guru;

# A. Berapa Rata-rata pada Jumlah Siswa Seluruh Provinsi
SELECT AVG(jumlah_siswa) FROM SEKOLAH_SammiALdhiYanto;

# B. Berapa Total pada Seluruh Siswa yang Tingkat Pendidikan SD
SELECT COUNT(tingkat_pendidikan) FROM SEKOLAH_SammiALdhiYanto WHERE tingkat_pendidikan = 'SD';

# C. Berapa Nilai Maksimum pada Jumlah Siswa Tingkat Pendidikan SMP
SELECT MAX(jumlah_siswa) FROM SEKOLAH_SammiALdhiYanto WHERE tingkat_pendidikan = 'SMP';

# D. Berapa Nilai Minimum Pada Jumlah Siswa yang berkelamin Wanita Tingkat Pendidikan SMK
SELECT MIN(jumlah_siswa) FROM SEKOLAH_SammiALdhiYanto WHERE jenis_kelamin = 'Perempuan' AND tingkat_pendidikan = 'SMK';

# E. Berapa Total Maksimum Siswa yang berkelamin Pria namun berasal dari Provinsi Jawa Barat
SELECT MAX(jumlah_siswa) FROM SEKOLAH_SammiALdhiYanto WHERE jenis_kelamin = 'Laki-laki' AND  provinsi = 'Jawa Barat';

# F. Berapa Banyak Jumlah Siswa yang Berasal Dari Riau yang Tingkat Pendidikan SMA dan
# Berikan Keterangan (alias) dengan nama “Total Siswa Provinsi Riau - SMA”
SELECT SUM(jumlah_siswa) as 'Total Siswa Provinsi Riau - SMA' from SEKOLAH_SammiALdhiYanto where provinsi = 'Riau' AND  tingkat_pendidikan = 'SMA';

```

# IMPORT FILE 
![import-data](https://user-images.githubusercontent.com/55814880/105795223-07d93600-5fbf-11eb-9ec8-7b96a10b7844.png)



### Section 2

**`© 2021 | sammidev `**
# SAMPLE BASIC SCHEME

```sql
CREATE TABLE SISWA (
    NIS VARCHAR(10) NOT NULL,
    NAMA VARCHAR(30) NOT NULL,
    ALAMAT VARCHAR(50) NOT NULL,
    KELAS VARCHAR(50) NOT NULL,
    PRIMARY KEY(NIS)
);


CREATE TABLE GURU (
    NIP VARCHAR(10) NOT NULL,
    NAMA VARCHAR(30) NOT NULL,
    ALAMAT VARCHAR(50) NOT NULL,
    TELP VARCHAR(15) NOT NULL UNIQUE,
    MATA_PELAJARAN VARCHAR(50) NOT NULL,
    PRIMARY KEY(NIP)
);


CREATE TABLE PEGAWAI (
    NIP VARCHAR(10) NOT NULL,
    NAMA VARCHAR(30) NOT NULL,
    ALAMAT VARCHAR(50) NOT NULL,
    JABATAN VARCHAR(50) NOT NULL,
    PRIMARY KEY(NIP)
);
```


### Pratikum 2

**`© 2021 | sammidev `**

# Buatlah sebuah database dengan nama db_universitas atau db_nama_mhs
```sql
CREATE DATABASE db_mhs_sammi;
```
# masuk ke database yang telah dibuat
```sql
USE db_mhs_sammi;
```

# Tabel mahasiswa
```sql
CREATE TABLE tb_mahasiswa_sammi(
    nim INT(8) PRIMARY KEY,
    nama_mhs CHAR(50),
    sex ENUM('L','P') DEFAULT 'L',
    alamat VARCHAR(50),
    kota VARCHAR(20) DEFAULT 'Purwokerto',
    asal_sma CHAR(30),
    nohp VARCHAR(12),
    login CHAR(20),
    pass CHAR(20),
    umur INT,
    kode_prodi CHAR(6),
    FOREIGN KEY fk0(kode_prodi) REFERENCES tb_prodi_sammi(kode_prodi)
);
```

# Tabel prodi
```sql
CREATE TABLE tb_prodi_sammi(
    kode_prodi CHAR(6) PRIMARY KEY,
    nama_prodi CHAR(30)
);
```

# Tabel mata_kuliah
float(4,2) = kita bisa insert data yg memiliki 4 buah digit angka dan 2 digit dibelakang koma
```sql
CREATE TABLE tb_mata_kuliah_sammi(
    mk_id CHAR(10) PRIMARY KEY,
    nama_mk CHAR(50),
    jumlah_jam FLOAT(4,2),
    sks INTEGER
);
```

# Tabel ruang
```sql
CREATE TABLE tb_ruang_sammi(
    ruang_id CHAR(3) PRIMARY KEY,
    nama_ruang CHAR(20),
    kapasitas INTEGER
);
```

# Tabel dosen
```sql
CREATE TABLE tb_dosen_sammi(
    nik INT(11) AUTO_INCREMENT PRIMARY KEY,
    inisial CHAR(3) UNIQUE KEY,
    nama_dosen CHAR(50),
    status ENUM('T','LB') DEFAULT 'T',
    sex ENUM('L','P') DEFAULT 'L',
    agama CHAR(20),
    login CHAR(20),
    pass CHAR(20),
    alamat VARCHAR(50),
    kota VARCHAR(20) DEFAULT 'Purwokerto',
    email VARCHAR(50),
    nohp VARCHAR(12),
    salary INT
);
```

# Tabel mengajar
```sql
CREATE TABLE tb_mengajar_sammi(
    id_mengajar INT AUTO_INCREMENT PRIMARY KEY,
    jam_ke INTEGER,
    hari VARCHAR(10),
    mk_id CHAR(10),
    inisial CHAR(3),
    kode_prodi CHAR(6),
    ruang_id CHAR(3),
    FOREIGN KEY fk1(mk_id) REFERENCES tb_mata_kuliah_sammi(mk_id),
    FOREIGN KEY fk2(inisial) REFERENCES tb_dosen_sammi(inisial),
    FOREIGN KEY fk3(kode_prodi) REFERENCES tb_prodi_sammi(kode_prodi),
    FOREIGN KEY fk4(ruang_id) REFERENCES tb_ruang_sammi(ruang_id)
);
```

# Tabel nilai
```sql
CREATE TABLE tb_nilai_sammi(
    nim INT,
    mk_id CHAR(10),
    kode_prodi CHAR(6),
    inisial CHAR(3),
    nilai_UTS INTEGER,
    nilai_UAS INTEGER,
    nilai_akhir INTEGER,
    FOREIGN KEY fk5(nim) REFERENCES tb_mahasiswa_sammi(nim),
    FOREIGN KEY fk6(mk_id) REFERENCES tb_mata_kuliah_sammi(mk_id),
    FOREIGN KEY fk7(kode_prodi) REFERENCES tb_prodi_sammi(kode_prodi),
    FOREIGN KEY fk8(inisial) REFERENCES tb_dosen_sammi(inisial)
);
```

```sql
# Tambahkan sebuah kolom Agama (varchar (10)) pada tabel mahasiswa
# sebagai kolom terakhir.
ALTER TABLE tb_mahasiswa_sammi ADD COLUMN agama VARCHAR(10);

# Tambahkan kolom rid(Char 10) di awal kolom (sebagai kolom pertama)
# pada tabel ruang.
ALTER TABLE tb_ruang_sammi ADD COLUMN rid CHAR(10) FIRST;

# Sisipkan sebuah kolom dengan nama grade (char) pada tabel nilai setelah
# kolom inisial.
ALTER TABLE tb_nilai_sammi ADD COLUMN grade CHAR AFTER inisial;

# Ubah nama tabel mahasiswa menjadi student.
ALTER TABLE tb_mahasiswa_sammi RENAME tb_student_sammi;

# Jadikan nim sebagai primary key pada table mahasiswa.
ALTER TABLE tb_mahasiswa_sammi ADD CONSTRAINT PRIMARY KEY(nim);

# Apa maksud dari Char(10)?
[HERE](https://hilwa.wordpress.com/2013/01/22/perbedaan-tipe-data-varchar-dengan-char-di-mysql/)

# Pada saat kita melihat struktur tabel dengan perintah desc, terdapat kolom
# Null yang berisi YES dan No. Apa maksudnya?
# => Kalau YES, maka field nya diizinkan untuk tidak diisi ketika menginputkan data
# => Kalau NO, maka field nya tidak diizinkan untuk tidak diisi ketika menginputkan data

# Tentukan kunci utama pada masing – masing tabel
# table mahasiswa = nim
# ..... yg mengandung primary key

# Tentukan kunci tamu pada tabel mengajar dan tabel nilai
# kunci tamu = foreign key
# mk_id
# inisial
# ....
```



### Pratikum 3

**`© 2021 | sammidev `**

# DB db_sammi
```sql
CREATE TABLE db_sammi;
```

# Aktifkan database
```sql
USE db_sammi;
```

# Tabel mahasiswa
```sql
CREATE TABLE tb_mahasiswa_sammi(
    nim INT(8) PRIMARY KEY,
    nama_mhs CHAR(50),
    sex ENUM('L','P') DEFAULT 'L',
    alamat VARCHAR(50),
    kota VARCHAR(20) DEFAULT 'Purwokerto',
    asal_sma CHAR(30),
    nohp VARCHAR(12),
    login CHAR(20),
    pass CHAR(20),
    umur INT,
    kode_prodi CHAR(6),
    FOREIGN KEY fk0(kode_prodi) REFERENCES tb_prodi_sammi(kode_prodi)
);
```

# Tabel prodi
```sql
CREATE TABLE tb_prodi_sammi(
    kode_prodi CHAR(6) PRIMARY KEY,
    nama_prodi CHAR(30)
);
```

# Tabel dosen
```sql
CREATE TABLE tb_dosen_sammi(
    nik INT(11) AUTO_INCREMENT PRIMARY KEY,
    inisial CHAR(3) UNIQUE KEY,
    nama_dosen CHAR(50),
    status ENUM('T','LB') DEFAULT 'T',
    sex ENUM('L','P') DEFAULT 'L',
    agama CHAR(20),
    login CHAR(20),
    pass CHAR(20),
    alamat VARCHAR(50),
    kota VARCHAR(20) DEFAULT 'Purwokerto',
    email VARCHAR(50),
    nohp VARCHAR(12),
    salary INT
);
```

## Isikan data – data (record) ke dalam tabel prodi
```sql
INSERT INTO tb_prodi_sammi VALUES 
('S1 IF','IF'),
('D3 TT','TT'),
('S1 TT','TT'),
('D1 PR','PR');
```

## Isikan data – data (record) ke dalam tabel mahasiswa
```sql
INSERT into tb_mahasiswa_sammi VALUES
('13120001','Anton', 'L', 'Jl. Jenderal Sudirman No.12','Brebes', 'SMA 1 Brebes', '081574568921','anton','anton','18','S1 IF'),
('13120002','Bany', 'L', 'Jl. Letnan Jenderal Sutoyo No.15','Tegal', 'SMA 1 Tegal', '081574568346','bany','bany','18','S1 IF'),
('13120003','Cika', 'P', 'Jl. Jenderal Sudirman No.38','Purwokerto', 'SMA 4 Purwokerto', '081874568000','cika','cika','17','S1 IF'),
('13120004','Doni', 'L', 'Jl. Pahlawan No. 4','Brebes', 'SMK N 1 Adiwerna', '081674568900','doni','doni','19','S1 TT'),
('13120005','Eka', 'P', 'Jl. Buntu No.01','Pekalongan', 'SMA 3 Pekalongan', '088874568945','eka','eka','17','S1 TT'),
('13120006','Fendi', 'L', 'Jl. Kemerdekaan No.15','Pemalang', 'SMA 1 Pemalang', '081257456892','fendi','fendi','18','D3 TT'),
('13120007','Galuh', 'P', 'Jl. Mawar Putih','Brebes', 'SMA 2 Brebes', '081273458921','galuh','galuh','18','D1 PR')
```

## Isikan data berikut ke dalam tabel dosen
```sql
INSERT into tb_dosen_sammi VALUES
('1','DS','Didi Supriyadi','T','L','Islam','didi','didi','Jl.Sunan Bonang RT 01/03 Banjaranyar','Brebes', 'didisupriyadi@st3telkom.ac.id', '085743622236','5000000'),
('2','STS','Sisilia Thya Safitri','T', 'P','Kristen','sisil','sisil', 'Jl. Antah berantah RT 001/005 Banjarbaru','Jambi', 'sisil@st3telkom.ac.id', '085875997546','5000000'),
('3','TW','Tenia Wahyuningrum','T', 'P','Islam','tenia','tenia', 'Jl. Ledug RT 01/03 Banyumas','Purwokerto', 'tenia@st3telkom.ac.id','085746795432','5500000'),
('4','DJ','Dwi Januarita AK','T', 'P','Islam','ita','ita', 'Jl. Sunan Kudus RT 01/03 Jekulo','Kudus', 'ita@st3telkom.ac.id', '085852829809','4000000'),
('5','IS','Irwan Susanto','T', 'L','Islam','irwan','irwan', 'Jl. Tanjung RT 01/03 Banyumas','Purwokerto', 'irwan@st3telkom.ac.id', '081327593529','5500000'),
('6','SL','Sarlan','LB', 'L', 'Islam', 'sarlan', 'sarlan', 'Jl. Jend. SudirmanRT 01/03 Banyumas','Purwokerto', 'sarlan@st3telkom.ac.id', '081634462738','3500000'),
('7','DN','Daniel','LB', 'L', 'Kristen', 'daniel', 'daniel', 'Jl. Tanjung RT 04/07 Banyumas','Purwokerto','daniel@st3telkom.ac.id', '081365047309','4500000')
```

## Tampilkan semua isi record tabel mahasiswa.
```sql
SELECT * FROM tb_mahasiswa_sammi;
```

## Ubah data salah satu nama mahasiswa (misal :Anton menjadi Dino)
```sql
UPDATE tb_mahasiswa_sammi SET nama_mhs = 'Dino' WHERE nama_mhs='Anton';
```

## Tampilkan satu baris data/record data yang telah diubah tadi yaitu record
dengan nama Dino saja.
```sql
SELECT * FROM tb_mahasiswa_sammi WHERE nama_mhs ='Dino';
```

## Hapus data mahasiswa yang bernama Dino.
```sql
DELETE FROM tb_mahasiswa_sammi WHERE nama_mhs = 'Dino';
```

## Tampilkan record/data mahasiswa yang usianya lebih dari atau sama
dengan 17 tahun.
```sql
SELECT  * FROM tb_mahasiswa_sammi WHERE umur >= 17;
```

## Tampilkan semua data dosen yang berjenis kelamin Pria dan agamanya
Islam.
```sql
SELECT * FROM tb_dosen_sammi WHERE sex='L' and agama='Islam';
```

## Dengan menggunakan satu perintah SELECT, tampilkan semua nama dosen yang berstatus Tetap dengan agamanya adalah Islam atau dosen Luar Biasa (LB) dengan agama kristen.
```sql
SELECT nama_dosen FROM tb_dosen_sammi WHERE status='T' and agama='islam' or status='LB' and agama='kristen';
```
