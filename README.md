**`© 2021 | sammidev `**

# Table of Contents

1. [**`Tugas 3`**](#section-1)
2. [**`UAS DATABASE`**](#section-2)
3. [**`Pratikum 2`**](#pratikum-2)
4. [**`Pratikum 3`**](#pratikum-3)
5. [**`Belajar JOIN`**](#belajar-join)
6. [**`Belajar relation`**](#belajar-relation)
7. [**`Belajar Mysql`**](#belajar-mysql)

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

### Belajar JOIN

**`© 2021 | sammidev `**

```sql
DROP DATABASE belajar_join;
CREATE DATABASE IF NOT EXISTS belajar_join;
USE belajar_join;

CREATE TABLE student (
    identifier INT(10),
    name VARCHAR(100),
    email VARCHAR(100),
    address VARCHAR(100),
    nip_dosen INT(10),
    PRIMARY KEY (identifier)
);

CREATE TABLE transaction (
    transaction_id INT(10),
    identifier INT(10),
    book VARCHAR(100),
    PRIMARY KEY (transaction_id)
);

CREATE TABLE dosen_pa (
    nip INT(10),
    name VARCHAR(100),
    email VARCHAR(100),
    PRIMARY KEY (nip)
);

ALTER TABLE transaction ADD COLUMN nip INT(100);
DESC transaction;

INSERT INTO dosen_pa VALUES
(1140020011,'Sukamto','Sukamto@gmail.com'),
(1140020211,'Efvy','efvy@gmail.com'),
(1140020311,'Fatayat','Fatayat@gmail.com');

INSERT INTO student VALUES
(21400200,'aqih','sammidev@gmail.com','bandung',1140020011),
(21400201,'ina','sammidev@gmail.com','jakarta',1140020011),
(21400202,'anto','sammidev@gmail.com','semarang',1140020011),
(21400203,'dani','sammidev@gmail.com','padang',1140020011),
(21400204,'jaka','ammidev@gmail.com','bandung',1140020011),
(21400205,'nara','sammidev@gmail.com','bandung',1140020011),
(21400206,'senta','sammidev@gmail.com','semarang',1140020311);

INSERT INTO transaction VALUES
(1,21400200,'uku Informatika', 1140020011),
(2,21400202,'Buku Teknik Elektro', 1242220011),
(3,21400203,'Buku Matematika',1140020011),
(4,21400206,'Buku Fisika',1140020311),
(5,21400207,'Buku Bahasa Indonesia',1143320211),
(6,21400210,'Buku Bahasa Daerah',1140020211),
(7,21400211,'Buku Kimia',1140020211);

SELECT * FROM student;
SELECT * FROM transaction;

# INNER JOIN
SELECT student.identifier, name, book FROM student INNER JOIN transaction t ON student.identifier = t.identifier;
SELECT student.identifier AS NIM_MAHASISWA, student.name AS NAMA_MAHASISWA ,dosen_pa.nip AS NIP_DOSEN_PA, dosen_pa.name AS NAMA_DOSEN_PA FROM student INNER JOIN dosen_pa ON student.nip_dosen = dosen_pa.nip;

# LEFT JOIN
SELECT * FROM student LEFT JOIN transaction t on student.identifier = t.identifier;
SELECT * FROM student LEFT JOIN dosen_pa t on student.nip_dosen = t.nip;

# RIGHT JOIN
SELECT * FROM student RIGHT JOIN transaction t on student.identifier = t.identifier;
SELECT * FROM student RIGHT JOIN dosen_pa t on student.nip_dosen = t.nip;

# lesson 2

CREATE TABLE IF NOT EXISTS `barang` (
  `id_barang` int(11) NOT NULL AUTO_INCREMENT,
  `id_kategori` smallint(6) NOT NULL,
  `nama_barang` varchar(255) CHARACTER SET latin1 NOT NULL,
  `harga` int(11) NOT NULL,
  `stok` int(11) NOT NULL,
  PRIMARY KEY (`id_barang`)
) ENGINE=InnoDB AUTO_INCREMENT=6 DEFAULT CHARSET=utf8 ROW_FORMAT=COMPACT;

INSERT INTO `barang` (`id_barang`, `id_kategori`, `nama_barang`, `harga`, `stok`) VALUES
	(1, 1, 'RAM', 230000, 4),
	(2, 1, 'Mainboard', 1250000, 7),
	(3, 1, 'Mouse', 80000, 6),
	(4, 3, 'Mousepad', 35000, 3),
	(5, 3, 'Keyboard', 80000, 5);

CREATE TABLE IF NOT EXISTS `pelanggan` (
  `id_pelanggan` int(11) NOT NULL AUTO_INCREMENT,
  `nama` varchar(50) DEFAULT NULL,
  `email` varchar(50) DEFAULT NULL,
  PRIMARY KEY (`id_pelanggan`)
) ENGINE=InnoDB AUTO_INCREMENT=5 DEFAULT CHARSET=latin1 ROW_FORMAT=COMPACT;

INSERT INTO `pelanggan` (`id_pelanggan`, `nama`, `email`) VALUES
	(1, 'Alfa', 'alfa@yahoo.com'),
	(2, 'Beta', 'beta@yahoo.com'),
	(3, 'Charlie', 'charlie@gmail.com'),
	(4, 'Delta', 'delta@gmail.com');

CREATE TABLE IF NOT EXISTS `penjualan` (
  `id_transaksi` int(11) NOT NULL AUTO_INCREMENT,
  `id_pelanggan` int(11) DEFAULT NULL,
  `tgl_transaksi` date NOT NULL,
  `total_transaksi` int(11) NOT NULL,
  PRIMARY KEY (`id_transaksi`),
  KEY `FK_penjualan_pelanggan` (`id_pelanggan`),
  CONSTRAINT `FK_penjualan_pelanggan` FOREIGN KEY (`id_pelanggan`) REFERENCES `pelanggan` (`id_pelanggan`) ON DELETE SET NULL ON UPDATE CASCADE
) ENGINE=InnoDB AUTO_INCREMENT=6 DEFAULT CHARSET=latin1 ROW_FORMAT=COMPACT;

INSERT INTO `penjualan` (`id_transaksi`, `id_pelanggan`, `tgl_transaksi`, `total_transaksi`) VALUES
	(1, 1, '2017-02-22', 230000),
	(2, 3, '2017-02-22', 195000),
	(3, 2, '2017-01-01', 1710000),
	(4, 1, '2017-02-04', 310000),
	(5, NULL, '2017-02-10', 80000);

CREATE TABLE IF NOT EXISTS `penjualan_detail` (
  `id_transaksi_detail` int(11) NOT NULL AUTO_INCREMENT,
  `id_transaksi` int(11) DEFAULT NULL,
  `id_barang` int(11) DEFAULT NULL,
  `jml_barang` smallint(6) DEFAULT NULL,
  `harga_satuan` int(11) DEFAULT NULL,
  PRIMARY KEY (`id_transaksi_detail`),
  KEY `FK_tb_penjualan_detail_tb_barang` (`id_barang`),
  KEY `FK_tb_penjualan_detail_tb_penjualan` (`id_transaksi`),
  CONSTRAINT `FK_tb_penjualan_detail_tb_barang` FOREIGN KEY (`id_barang`) REFERENCES `barang` (`id_barang`) ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT `FK_tb_penjualan_detail_tb_penjualan` FOREIGN KEY (`id_transaksi`) REFERENCES `penjualan` (`id_transaksi`) ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE=InnoDB AUTO_INCREMENT=10 DEFAULT CHARSET=utf8;

INSERT INTO `penjualan_detail` (`id_transaksi_detail`, `id_transaksi`, `id_barang`, `jml_barang`, `harga_satuan`) VALUES
	(1, 1, 1, 1, 230000),
	(2, 2, 4, 1, 35000),
	(3, 2, 5, 2, 80000),
	(4, 3, 2, 1, 1250000),
	(5, 3, 1, 2, 230000),
	(6, 4, 4, 2, 35000),
	(7, 4, 5, 1, 80000),
	(8, 4, 3, 2, 80000),
	(9, 5, 3, 1, 80000);

SELECT * FROM barang;
SELECT * FROM pelanggan;
SELECT * FROM penjualan;
SELECT * FROM penjualan_detail;

SELECT pl.id_pelanggan, pl.nama, tgl_transaksi, total_transaksi from pelanggan pl JOIN penjualan p on pl.id_pelanggan = p.id_pelanggan;
SELECT pl.id_pelanggan, nama, tgl_transaksi, total_transaksi FROM pelanggan pl LEFT JOIN penjualan USING(id_pelanggan);
SELECT pl.id_pelanggan, nama, tgl_transaksi, total_transaksi FROM pelanggan pl RIGHT JOIN penjualan USING(id_pelanggan);
SELECT pl.id_pelanggan, nama, id_transaksi, tgl_transaksi, total_transaksi FROM pelanggan pl, penjualan pn WHERE pl.id_pelanggan = pn.id_pelanggan;



DROP DATABASE belajar_join;
CREATE DATABASE IF NOT EXISTS belajar_join;
USE belajar_join;

CREATE TABLE customer (
    customer_id INT PRIMARY KEY AUTO_INCREMENT,
    customer_name VARCHAR(100) NOT NULL,
    customer_email VARCHAR(100) NOT NULL
);

CREATE TABLE product (
    product_id INT PRIMARY KEY AUTO_INCREMENT,
    product_name VARCHAR(100) NOT NULL,
    product_price DOUBLE NOT NULL
);

CREATE TABLE wishlist (
    wishlist_id INT PRIMARY KEY AUTO_INCREMENT,
    product_id INT NOT NULL,
    customer_id INT NOT NULL
);

ALTER TABLE wishlist ADD CONSTRAINT fk_customer_wishlist FOREIGN KEY (customer_id) REFERENCES customer(customer_id);
ALTER TABLE wishlist ADD CONSTRAINT fk_product_wishlist FOREIGN KEY (product_id) REFERENCES product(product_id);


INSERT INTO customer (customer_name, customer_email) VALUES
('sammidev 1', 'ammidev1@gmail.com'),
('sammidev 2', 'sammidev2@gmail.com'),
('sammidev 3', 'sammidev3@gmail.com'),
('sammidev 4', 'sammidev4@gmail.com'),
('sammidev 5', 'sammidev5@gmail.com'),
('sammidev 6', 'sammidev6@gmail.com');

INSERT INTO product (product_name, product_price) VALUES
('product a 1', 10.0),
('product b 1', 11.0),
('product c 1', 12.0),
('product d 1', 13.0),
('product e 1', 14.0);

INSERT INTO wishlist (product_id, customer_id) VALUES
(1,1),
(2,1),
(2,2),
(3,2),
(4,4);

SELECT customer_name  AS CUSTOMER_NAME,
       customer_email AS CUSTOMER_EMAIL,
       product_name   AS PRODUCT_NAME,
       product_price  AS PRODUCT_PRICE FROM wishlist w
           JOIN product     p on p.product_id = w.product_id
           JOIN customer    c on c.customer_id = w.customer_id;
```



### Belajar relation

**`© 2021 | sammidev `**


**1 -> 1**
```sql
DROP DATABASE belajar_relation;
CREATE DATABASE belajar_relation;
USE belajar_relation;

CREATE TABLE customer(
    id INT NOT NULL AUTO_INCREMENT,
    email VARCHAR(100)  NOT NULL,
    first_name VARCHAR(100)  NOT NULL,
    last_name VARCHAR(100)  NOT NULL,
    PRIMARY KEY (id)
);

CREATE TABLE wallet
(
    id          INT NOT NULL AUTO_INCREMENT,
    customer_id INT NOT NULL,
    balance     INT NOT NULL DEFAULT 0,
    PRIMARY KEY (id),
    UNIQUE KEY fk_id_customer_unique (customer_id),
    CONSTRAINT fk_wallet_customer FOREIGN KEY (customer_id) REFERENCES belajar_relation.customer (id)
);

INSERT INTO customer(email, first_name, last_name) VALUES
('sammidev1@gmail.com','sammi1','dev1'),
('sammidev2@gmail.com','sammi2','dev2'),
('sammidev3@gmail.com','sammi3','dev3'),
('sammidev4@gmail.com','sammi4','dev4');

SELECT * FROM customer;

INSERT INTO wallet(customer_id, balance) VALUES
(1,100000),
(2,200000),
(3,300000),
(4,400000);


```
**1 -> n**
```sql
CREATE TABLE categories (
    id VARCHAR(100) NOT NULL,
    name VARCHAR(100) NOT NULL,
    PRIMARY KEY (id)
) ENGINE = InnoDB;

CREATE TABLE product (
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    product_name VARCHAR(100) NOT NULL,
    product_price INT NOT NULL
);

ALTER TABLE product ADD COLUMN category_id VARCHAR(100);
ALTER TABLE product ADD CONSTRAINT dk_product_category FOREIGN KEY (category_id) REFERENCES categories(id);

INSERT INTO categories(id, name) VALUES
('aaa','SkinCare'),
('bbb','Dapur'),
('ccc','Elektronik');

INSERT INTO product (product_name, product_price, category_id) VALUES
('product A', 100, 'aaa'),
('product B', 200, 'aaa'),
('product C', 300, 'bbb'),
('product D', 400, 'bbb'),
('product E', 500, 'ccc');

SELECT * FROM product JOIN categories on product.category_id = categories.id;
```
**m -> n**
*COMING SOON*


**tables samples**
```sql
CREATE TABLE IF NOT EXISTS customer (
  `customer_id` int(11) NOT NULL AUTO_INCREMENT,
  `customer_full_name` varchar(30) NOT NULL,
  `customer_email` varchar(50) NOT NULL,
  `customer_phone_number` varchar(15) NOT NULL,
  `customer_username` varchar(30) NOT NULL,
  `customer_password` varchar(30) NOT NULL,
  `account_status` int(1) NOT NULL DEFAULT 1,
  PRIMARY KEY (`customer_id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1 AUTO_INCREMENT=1 ;

CREATE TABLE IF NOT EXISTS menu (
  `menu_id` int(11) NOT NULL AUTO_INCREMENT,
  `menu_name` varchar(100) NOT NULL,
  `price` float NOT NULL,
  `menu_type_id` int(11) NOT NULL,
  `ingredients` varchar(500) NOT NULL,
  `menu_status` int(1) NOT NULL,
  PRIMARY KEY (`menu_id`),
  KEY `menu_type_id` (`menu_type_id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1 AUTO_INCREMENT=1 ;

CREATE TABLE IF NOT EXISTS menu_type (
  `menu_type_id` int(11) NOT NULL AUTO_INCREMENT,
  `type_name` varchar(50) NOT NULL,
  `description` varchar(100) NOT NULL,
  PRIMARY KEY (`menu_type_id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1 AUTO_INCREMENT=1 ;

CREATE TABLE IF NOT EXISTS orders (
  `order_id` int(11) NOT NULL AUTO_INCREMENT,
  `customer_id` int(11) NOT NULL,
  `order_date` datetime NOT NULL,
  `total_price` float,
  `order_location` varchar(200) NOT NULL,
  `order_status` int(1) NOT NULL DEFAULT 0,
  PRIMARY KEY (`order_id`),
  KEY `customer_id` (`customer_id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1 AUTO_INCREMENT=1 ;

CREATE TABLE IF NOT EXISTS order_details (
  `order_details_id` int(11) NOT NULL AUTO_INCREMENT,
  `order_id` int(11) NOT NULL,
  `menu_id` int(11) NOT NULL,
  `quantity` int(11) NOT NULL,
  `total_price` float,
  PRIMARY KEY (`order_details_id`),
  KEY `order_id` (`order_id`,`menu_id`),
  KEY `menu_id` (`menu_id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1 AUTO_INCREMENT=1 ;

CREATE TABLE IF NOT EXISTS payment (
  `payment_id` int(11) NOT NULL AUTO_INCREMENT,
  `order_id` int(11) NOT NULL,
  `amount` float NOT NULL,
  `payment_type_id` int(11) NOT NULL,
  `payment_date` datetime NOT NULL,
  `payment_status` int(1) NOT NULL DEFAULT 0,
  PRIMARY KEY (`payment_id`),
  KEY `order_id` (`order_id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1 AUTO_INCREMENT=1 ;

CREATE TABLE IF NOT EXISTS rating (
  `rating_id` int(11) NOT NULL AUTO_INCREMENT,
  `menu_id` int(11) NOT NULL,
  `score` int(1) NOT NULL,
  `remarks` varchar(100) NOT NULL,
  `date_recorded` datetime NOT NULL,
  `customer_id` int(11) NOT NULL,
  PRIMARY KEY (`rating_id`),
  KEY `menu_id` (`menu_id`),
  KEY `customer_id` (`customer_id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1 AUTO_INCREMENT=1 ;

ALTER TABLE menu
  ADD CONSTRAINT `tblmenu_ibfk_1` FOREIGN KEY (`menu_type_id`) REFERENCES menu_type (`menu_type_id`) ON DELETE CASCADE ON UPDATE CASCADE;

ALTER TABLE orders
  ADD CONSTRAINT `tblorder_ibfk_2` FOREIGN KEY (`customer_id`) REFERENCES customer (`customer_id`) ON DELETE CASCADE ON UPDATE CASCADE;

ALTER TABLE order_details
  ADD CONSTRAINT `tblorderdetails_ibfk_2` FOREIGN KEY (`order_id`) REFERENCES orders (`order_id`) ON DELETE CASCADE ON UPDATE CASCADE,
  ADD CONSTRAINT `tblorderdetails_ibfk_1` FOREIGN KEY (`menu_id`) REFERENCES menu (`menu_id`) ON DELETE CASCADE ON UPDATE CASCADE;

ALTER TABLE payment
  ADD CONSTRAINT `tblpayment_ibfk_2` FOREIGN KEY (`order_id`) REFERENCES orders (`order_id`) ON DELETE CASCADE ON UPDATE CASCADE;

ALTER TABLE rating
  ADD CONSTRAINT `tblrating_ibfk_2` FOREIGN KEY (`customer_id`) REFERENCES customer (`customer_id`) ON DELETE CASCADE ON UPDATE CASCADE,
  ADD CONSTRAINT `tblrating_ibfk_1` FOREIGN KEY (`menu_id`) REFERENCES menu (`menu_id`) ON DELETE CASCADE ON UPDATE CASCADE;
```

**tables samples 2**
```sql
CREATE TABLE `major` (
    `id` varchar(50) NOT NULL,
    `created_at` datetime(3) DEFAULT NULL,
    `updated_at` datetime(3) DEFAULT NULL,
    `major` varchar(100) NOT NULL,
    `faculty` varchar(100) NOT NULL,
    `faculty_short` varchar(5) NOT NULL,
    `major_short` varchar(5) NOT NULL,
    PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

CREATE TABLE `graduates` (
    `id` varchar(50) NOT NULL,
    `created_at` datetime(3) DEFAULT NULL,
    `updated_at` datetime(3) DEFAULT NULL,
    `identifier` int(10) unsigned DEFAULT NULL,
    `name` varchar(255) NOT NULL,
    `nick_name` varchar(255) NOT NULL,
    `thesis_title` varchar(1024) NOT NULL,
    `incoming` smallint(6) NOT NULL,
    `major_id` varchar(50) NOT NULL,
    `instagram` varchar(255) DEFAULT NULL,
    `linkedin` varchar(255) DEFAULT NULL,
    `twitter` varchar(255) DEFAULT NULL,
    `pob` varchar(255) DEFAULT NULL,
    `dob` date DEFAULT NULL,
    `photo` varchar(255) DEFAULT NULL,
    PRIMARY KEY (`id`),
    UNIQUE KEY `identifier` (`identifier`),
    KEY `fk_graduates_major` (`major_id`),
    CONSTRAINT `fk_graduates_major` FOREIGN KEY (`major_id`) REFERENCES `major` (`id`) ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

CREATE TABLE `content` (
    `id` varchar(50) NOT NULL,
    `created_at` datetime(3) DEFAULT NULL,
    `updated_at` datetime(3) DEFAULT NULL,
    `graduates_id` varchar(50) NOT NULL,
    `organization_id` varchar(50) DEFAULT NULL,
    `type` varchar(16) NOT NULL,
    `headings` varchar(255) NOT NULL,
    `details` text DEFAULT NULL,
    `image` varchar(255) DEFAULT NULL,
    PRIMARY KEY (`id`),
    KEY `fk_content_graduates` (`graduates_id`),
    CONSTRAINT `fk_content_graduates` FOREIGN KEY (`graduates_id`) REFERENCES `graduates` (`id`) ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

CREATE TABLE `organization` (
    `id` varchar(50) NOT NULL,
    `created_at` datetime(3) DEFAULT NULL,
    `updated_at` datetime(3) DEFAULT NULL,
    `name` varchar(255) NOT NULL,
    `slug` varchar(128) NOT NULL,
    `category` varchar(64) NOT NULL,
    `logo` varchar(255) NOT NULL,
    `poster_appreciation` varchar(255) DEFAULT NULL,
    `writing_appreciation` text DEFAULT NULL,
    `video_appreciation` varchar(255) DEFAULT NULL,
    `faculty_short` varchar(5) DEFAULT NULL,
    PRIMARY KEY (`id`),
    UNIQUE KEY `slug` (`slug`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

CREATE TABLE `message` (
    `id` varchar(50) NOT NULL,
    `created_at` datetime(3) DEFAULT NULL,
    `updated_at` datetime(3) DEFAULT NULL,
    `receiver_id` varchar(50) NOT NULL,
    `message` text NOT NULL,
    `sender` varchar(255) NOT NULL,
    PRIMARY KEY (`id`),
    KEY `fk_message_receiver` (`receiver_id`),
    CONSTRAINT `fk_message_receiver` FOREIGN KEY (`receiver_id`) REFERENCES `graduates` (`id`) ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

CREATE TABLE `view` (
    `id` varchar(50) NOT NULL,
    `graduates_id` varchar(50) NOT NULL,
    `ip` varchar(255) NOT NULL,
    `access_time` datetime(3) DEFAULT NULL,
    PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
```



### Belajar MySQL
```sql
CREATE TABLE customer (
    customer_id BIGINT NOT NULL AUTO_INCREMENT,
    customer_name VARCHAR(50) NOT NULL,
    address VARCHAR(50),
    phone_number CHAR (12) UNICODE,
    email VARCHAR (50) UNICODE,
    PRIMARY KEY(customer_id)
);

DESC customer;

INSERT INTO customer(customer_name, address, phone_number, email)
VALUES ('sam1', 'sammidev1 address', '000000000000', 'sammidev1@gmail.com'),
       ('sam2', 'sammidev2 address', '000000000001', 'sammidev2@gmail.com'),
       ('sam3', 'sammidev3 address', '000000000002', 'sammidev3@gmail.com'),
       ('sam4', 'sammidev4 address', '000000000003', 'sammidev4@gmail.com'),
       ('sam5', 'sammidev5 address', '000000000004', 'sammidev5@gmail.com');

UPDATE customer SET customer_name = 'sammidev' WHERE customer_id = 1;

INSERT INTO customer(customer_name, address, phone_number, email)
VALUES ('sam5','add6', '0000', 'sammidev4@yahoo.com');

SELECT * FROM customer WHERE email LIKE '%@gmail.com';
SELECT * FROM customer WHERE email LIKE '%@yahoo.com';

SELECT * FROM customer ORDER BY customer_id;
SELECT * FROM customer ORDER BY customer_id DESC;

SELECT * FROM customer LIMIT 3;
SELECT * FROM customer LIMIT 2,3;
SELECT * FROM customer LIMIT 3 OFFSET 1;
SELECT COUNT(*) FROM customer;

SELECT customer_id, CONCAT(customer_name, '_', email) AS nama_email FROM customer;
SELECT SUBSTRING(customer_name, 1, 4) FROM customer;
SELECT CONCAT_WS(', ', customer_id, customer_name, email) FROM customer;
SELECT customer_name, LENGTH(customer_name) as customer_name_length FROM customer;
SELECT LEFT(customer_name, 4) FROM customer where customer_id = 1;
SELECT RIGHT(customer_name, 4) FROM customer where customer_id = 1;

SELECT LEFT(customer_name, LENGTH(customer_name)/2) as leftname,
       RIGHT(customer_name, length(customer_name)/2) as rightname,
       customer_name as fullname
from customer;

SELECT LTRIM('    sammidev        ') as ltrim;
SELECT RTRIM('    sammidev        ') as rtring;
SELECT TRIM('    sammidev        ') as trim;
SELECT REPLACE('aaa', 'a','b');
SELECT REPEAT('i love u', 3);
SELECT REVERSE('apa');
SELECT LCASE('SAMMIDEV');
SELECT UCASE('sammidev');


SELECT NOW();
SELECT SYSDATE();

SELECT MONTH('2001-10-20');
SELECT YEAR('2001-10-20');
SELECT WEEK('2001-10-20');
SELECT WEEKDAY('2001-10-20');
SELECT DAYNAME('2001-10-20');
SELECT DAYNAME('2002-01-01');
SELECT HOUR(NOW());
SELECT MINUTE(NOW());
SELECT SECOND(NOW());


SELECT DATE_ADD(now(), INTERVAL 1 DAY);
SELECT DATE_ADD(now(), INTERVAL 2 HOUR);
SELECT NOW() as sekarang,  DATE_ADD(now(), interval 1 hour) as 'satu_jam_kemudian';

SELECT DATE_FORMAT (now(), '%a, %d-%M-%Y %H:%i:%s');

SELECT 1+1;
SELECT 1-1;
SELECT 1*1;
SELECT 1/1;
SELECT 1%1;
SELECT ABS(-1);
SELECT FLOOR(3.8);
SELECT CEIL(3.8);
SELECT ROUND(3.6);
SELECT ROUND(3.7);
SELECT 32 != 32;
SELECT 32 = 32;
SELECT POW(2,5) = 32;
SELECT RAND(2);
SELECT TRUNCATE(10.123131231231241, 3) as 3_dec;
SELECT GREATEST(2,3) as 2_vs_3;
SELECT COUNT(*) FROM customer;
SELECT MAX(customer_id) FROM customer;
SELECT MIN(customer_id) FROM customer;
SELECT SUM(customer_id) FROM customer;
SELECT AVG(customer_id) FROM customer;
SELECT current_user();
SELECT CURRENT_DATE;
SELECT CURRENT_TIMESTAMP;
SELECT USER();
SELECT SYSTEM_USER();
SELECT SESSION_USER();
SELECT PASSWORD('sammidev');
SELECT PASSWORD('sammidev') = PASSWORD('sammidev');
SELECT ENCODE('sam', 'dev');
SELECT MD5('dev');
SELECT LAST_INSERT_ID();
SELECT VERSION();

DROP TABLE customer;

# advance
CREATE TABLE produk (
    id_produk varchar(5) NOT NULL,
    nm_produk varchar(30) NOT NULL,
    satuan varchar(10) NOT NULL,
    harga decimal(10,0) NOT NULL default '0',
    stock int(3) NOT NULL default '0',
    PRIMARY KEY (id_produk)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

CREATE TABLE pelanggan (
    id_pelanggan varchar(5) NOT NULL,
    nm_pelanggan varchar(40) NOT NULL,
    alamat text NOT NULL,
    telepon varchar(20) NOT NULL,
    email varchar(50) NOT NULL,
    PRIMARY KEY (id_pelanggan)
) ENGINE=InnoDB DEFAULT CHARSET=latin1 CHECKSUM=1 DELAY_KEY_WRITE=1 ROW_FORMAT=DYNAMIC;

CREATE TABLE pesan (
    id_pesan int(5) NOT NULL auto_increment,
    id_pelanggan varchar(5) NOT NULL,
    tgl_pesan date NOT NULL,
    PRIMARY KEY (id_pesan),
    KEY id_pelanggan (id_pelanggan),
    CONSTRAINT pesan_ibfk_1 FOREIGN KEY (id_pelanggan)
    REFERENCES pelanggan (id_pelanggan)
) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=latin1;

CREATE TABLE faktur (
    id_faktur int(5) NOT NULL auto_increment,
    id_pesan int(5) NOT NULL,
    tgl_faktur date NOT NULL,
    PRIMARY KEY (id_faktur),
    KEY id_pesan (id_pesan),
    CONSTRAINT faktur_ibfk_1 FOREIGN KEY (id_pesan)
    REFERENCES pesan (id_pesan)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

CREATE TABLE kuitansi (
    id_kuitansi int(5) NOT NULL auto_increment,
    id_faktur int(5) NOT NULL,
    tgl_kuitansi date NOT NULL,
    PRIMARY KEY (id_kuitansi),
    KEY FK_kuitansi (id_faktur),
    CONSTRAINT FK_kuitansi FOREIGN KEY (id_faktur)
    REFERENCES faktur (id_faktur)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

CREATE TABLE detil_pesan (
    id_pesan int(5) NOT NULL,
    id_produk varchar(5) NOT NULL,
    jumlah int(5) NOT NULL default '0',
    harga decimal(10,0) NOT NULL default '0',
    PRIMARY KEY (id_pesan,id_produk),
    KEY FK_detil_pesan (id_produk),
    KEY id_pesan (id_pesan),
    CONSTRAINT FK_detil_pesan FOREIGN KEY (id_produk) REFERENCES produk (id_produk),
    CONSTRAINT FK_detil_pesan2 FOREIGN KEY (id_pesan) REFERENCES pesan (id_pesan)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

SHOW TABLES;

INSERT INTO pelanggan(id_pelanggan, nm_pelanggan, alamat, telepon, email)
VALUES ('p0001', 'sammi', 'padang', '00001', 'sammi@gmail.com'),
       ('p0002', 'izzah', 'riau', '00002','izzah@gmail.com'),
       ('p0003', 'adid', 'talu', '00003', 'adid@gmail.com');


INSERT INTO pesan(id_pelanggan, tgl_pesan)
VALUES ('p0001', NOW()),
       ('p0002', NOW()),
       ('p0003', NOW()),
       ('p0001', DATE_ADD(NOW(), INTERVAL 1 WEEK)),
       ('p0001', DATE_ADD(NOW(), INTERVAL 1 DAY ));

SELECT * FROM pelanggan;
SELECT * FROM pesan;

SELECT pelanggan.nm_pelanggan as nama, pelanggan.email, pesan.tgl_pesan as tanggal FROM pelanggan, pesan WHERE pelanggan.id_pelanggan = pesan.id_pelanggan;

SELECT p.id_pelanggan as id_pelanggan,
       p.nm_pelanggan as nama,
       p.email as email,
       a.id_pesan as id_pesanan,
       a.tgl_pesan as tanggal FROM pelanggan p
           INNER JOIN pesan a on p.id_pelanggan = a.id_pelanggan ORDER BY tanggal DESC;

INSERT INTO pelanggan(id_pelanggan, nm_pelanggan, alamat, telepon, email)
 VALUES ('p0004', 'hantu', 'jakarta', '00004', 'hantu@gmail.com');


SELECT p.id_pelanggan as id_pelanggan,
       p.nm_pelanggan as nama,
       p.email as email,
       a.id_pesan as id_pesanan,
       a.tgl_pesan as tanggal FROM pelanggan p
           LEFT JOIN  pesan a on p.id_pelanggan = a.id_pelanggan;

SELECT p.id_pelanggan as id_pelanggan,
       p.nm_pelanggan as nama,
       p.email as email,
       a.id_pesan as id_pesanan,
       a.tgl_pesan as tanggal FROM pelanggan p
           RIGHT JOIN  pesan a on p.id_pelanggan = a.id_pelanggan;


INSERT INTO produk(id_produk, nm_produk, satuan, harga, stock)
VALUES ('prod4', 'product e', 'rupiah', 10000, '10'),
       ('prod5', 'product f', 'rupiah', 650000, '20'),
       ('prod6', 'product g', 'rupiah', 30000, '30');

SELECT * FROM produk;
desc detil_pesan;
desc produk;
SELECT id_pesan FROM pesan;

INSERT INTO detil_pesan(id_pesan, id_produk, jumlah, harga)
VALUES (4, 'prod1', 1, 10000),
       (7, 'prod2', 3, 650000),
       (8, 'prod3', 4, 30000);

SELECT * FROM pelanggan;
SELECT * FROM pesan;
SELECT * FROM produk;
SELECT * FROM detil_pesan;

SELECT pelanggan.id_pelanggan as ID_PELANGGAN,
       pelanggan.nm_pelanggan as NAMA_PELANGGAN,
       pelanggan.email as EMAIL_PELANGGAN,
       pesan.id_pesan as ID_PESANAN,
       detil_pesan.id_produk as ID_PRODUK,
       produk.nm_produk as NAMA_PRODUK,
       produk.harga as HARGA_PRODUK,
       detil_pesan.jumlah AS JUMLAH_PRODUK
    FROM pelanggan JOIN pesan
    ON pelanggan.id_pelanggan = pesan.id_pelanggan
    JOIN detil_pesan
    ON pesan.id_pesan = detil_pesan.id_pesan
    JOIN produk
    ON detil_pesan.id_produk = produk.id_produk;

INSERT INTO detil_pesan(id_pesan, id_produk, jumlah, harga)
VALUES (4, 'prod4', 1, 1 * 10000),
       (5, 'prod5', 3, 3 * 650000),
       (6, 'prod6', 4, 4 * 30000);

SELECT pelanggan.id_pelanggan as ID_PELANGGAN,
       pelanggan.nm_pelanggan as NAMA_PELANGGAN,
       pelanggan.email as EMAIL_PELANGGAN,
       pesan.id_pesan as ID_PESANAN,
       detil_pesan.id_produk as ID_PRODUK,
       produk.nm_produk as NAMA_PRODUK,
       produk.harga as HARGA_PRODUK,
       detil_pesan.jumlah AS JUMLAH_PRODUK
    FROM pelanggan JOIN pesan
    ON pelanggan.id_pelanggan = pesan.id_pelanggan
    JOIN detil_pesan
    ON pesan.id_pesan = detil_pesan.id_pesan
    JOIN produk
    ON detil_pesan.id_produk = produk.id_produk;



SELECT pesan.id_pesan,
       pesan.tgl_pesan
FROM pesan, detil_pesan
WHERE pesan.id_pesan = detil_pesan.id_pesan;

desc pesan;

SELECT pesan.id_pesan,
       pesan.tgl_pesan,
       pesan.id_pelanggan,
       SUM(detil_pesan.jumlah) as jumlah
FROM pesan, detil_pesan
WHERE pesan.id_pesan = detil_pesan.id_pesan
GROUP BY id_pesan;

SELECT pesan.id_pesan, COUNT(detil_pesan.id_produk) as
jumlah
FROM pesan, detil_pesan
WHERE pesan.id_pesan=detil_pesan.id_pesan
GROUP BY pesan.id_pesan
HAVING jumlah > 1;


SELECT id_pelanggan, nm_pelanggan FROM pelanggan
WHERE id_pelanggan IN (SELECT id_pelanggan FROM pesan);

SELECT id_pesan, jumlah from detil_pesan where jumlah = (
    select max(jumlah) from detil_pesan
);


SELECT * FROM pelanggan ORDER BY RAND() LIMIT 2;

SET AUTOCOMMIT = 0;
BEGIN;
INSERT INTO pelanggan(id_pelanggan, nm_pelanggan, alamat, telepon, email)
VALUES ('p10', 'rahmatul', 'riau', '000', 'rahma@gmail.com');
SET @id := LAST_INSERT_ID();
COMMIT;

SELECT * FROM pelanggan WHERE email = 'rahma@gmail.com';

USE mysql;
SHOW TABLES;
SELECT * FROM user;

GRANT ALL PRIVILEGES ON *.* TO monty@localhost
IDENTIFIED BY 'qwerty' WITH GRANT OPTION;

GRANT USAGE ON *.* TO adinda@192.168.1.5
IDENTIFIED BY 'qwerty';

GRANT ALL PRIVILEGES ON mysql.* TO admin@localhost
IDENTIFIED BY 'qwerty';

GRANT ALL PRIVILEGES ON penjualan.* TO
adinda@192.168.1.5;
FLUSH PRIVILEGES;

GRANT CREATE ON penjualan.* TO admin@localhost;
FLUSH PRIVILEGES;

REVOKE CREATE ON penjualan.* FROM admin@localhost;
FLUSH PRIVILEGES;

UPDATE user SET Password=PASSWORD(‘123’) WHERE
User=’admin’ AND Host=’localhost’;
SET PASSWORD FOR admin@localhost = PASSWORD (‘123’);
FLUSH PRIVILEGES;

USE belajar_mysql;

DELIMITER $$
CREATE TRIGGER penjualan.before_insert BEFORE INSERT ON
penjualan.pelanggan
FOR EACH ROW BEGIN
INSERT INTO `log` (description, `datetime`, user_id)
VALUES (CONCAT('Insert data ke tabel pelanggan id_plg
= ', NEW.id_pelanggan), now(), user());
END;
$$
DELIMITER ;

DROP TRIGGER penjualan.before_insert;

CREATE VIEW `data_plg` AS
(select id_pelanggan, nm_pelanggan, telepon
from `pelanggan` order by `nm_pelanggan`);

SELECT * FROM data_plg;

CREATE VIEW lap_jumlah_brg_transaksi
AS (SELECT pesan.id_pesan, pesan.tgl_pesan,
    pelanggan.id_pelanggan, pelanggan.nm_pelanggan,
    detil_pesan.jumlah
    FROM pesan, detil_pesan, pelanggan
    WHERE pesan.id_pesan=detil_pesan.id_pesan AND
    pelanggan.id_pelanggan=pesan.id_pelanggan
    GROUP BY pesan.id_pesan);

SELECT * FROM lap_jumlah_brg_transaksi;

DROP VIEW data_plg;
DROP VIEW lap_jumlah_brg_transaksi;

DELIMITER $$
    CREATE PROCEDURE hello()
    BEGIN
        SELECT "Hello World!";
    END$$
DELIMITER ;

CALL hello();


DELIMITER $$
    CREATE PROCEDURE jumlahPelanggan()
    BEGIN
        SELECT COUNT(*) FROM pelanggan;
    END$$
DELIMITER ;

CALL jumlahPelanggan();

DELIMITER $$
    CREATE PROCEDURE
    jumlahItemBarang (pelanggan VARCHAR(5))
    BEGIN
        SELECT SUM(detil_pesan.jumlah)
            FROM pesan, detil_pesan
            WHERE pesan.id_pesan=detil_pesan.id_pesan
        AND pesan.id_pelanggan=pelanggan;
    END$$
DELIMITER ;

CALL jumlahItemBarang('p0001');

DELIMITER $$
    CREATE FUNCTION jumlahStockBarang(produk VARCHAR(5))
    RETURNS INT
    BEGIN
        DECLARE jumlah INT;
        SELECT COUNT(*) INTO jumlah FROM produk
        WHERE id_produk=produk;
    RETURN jumlah;
    END$$
DELIMITER ;

SELECT * FROM produk;
SELECT jumlahStockBarang('prod6');

DELIMITER $$
    CREATE FUNCTION hitungUmur (lahir DATE)
    RETURNS INT
    BEGIN
        DECLARE thn_sekarang, thn_lahir INT;
        SET thn_sekarang = YEAR(now());
        SET thn_lahir = YEAR (lahir);
        RETURN thn_sekarang - thn_lahir;
    END$$
DELIMITER ;

SELECT hitungUmur(DATE('2001-10-20'));


DELIMITER $$
    CREATE FUNCTION cekPelanggan (pelanggan varchar(5))
    RETURNS VARCHAR (100)
    BEGIN
        DECLARE jumlah INT;
        SELECT COUNT(id_pesan) INTO jumlah FROM pesan
        WHERE id_pelanggan=pelanggan;
            IF (jumlah > 0) THEN
            RETURN CONCAT("Anda sudah bertransaksi sebanyak ",
            jumlah, " kali");
        ELSE
            RETURN "Anda belum pernah melakukan transaksi";
        END IF;
    END$$
DELIMITER ;

SELECT * FROM pelanggan;
SELECT cekPelanggan('p0001');

DELIMITER $$
CREATE FUNCTION getDiskon(jumlah INT) RETURNS int(11)
    BEGIN
        DECLARE diskon INT;
        CASE
            WHEN (jumlah >= 100) THEN
                SET diskon = 10;
            WHEN (jumlah >= 50 AND jumlah < 100) THEN
                SET diskon = 5;
            WHEN (jumlah >= 20 AND jumlah < 50) THEN
                SET diskon = 3;
            ELSE SET diskon = 0;
        END CASE;
        RETURN diskon;
    END$$
DELIMITER ;
```

#Online Banking

```sql
CREATE DATABASE  IF NOT EXISTS onlinebanking
USE onlinebanking;
```

```sql
DROP TABLE IF EXISTS primary_account;
CREATE TABLE primary_account
(
    id              bigint(20) NOT NULL AUTO_INCREMENT,
    account_balance decimal(19, 2) DEFAULT NULL,
    account_number  int(11) NOT NULL,
    PRIMARY KEY (id)
) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8;
```

```sql
LOCK TABLES primary_account WRITE;
INSERT INTO primary_account
VALUES (1, 1700.00, 11223146),
       (2, 0.00, 11223150);
UNLOCK TABLES;
```

```sql
DROP TABLE IF EXISTS savings_account;
CREATE TABLE savings_account
(
    id              bigint(20) NOT NULL AUTO_INCREMENT,
    account_balance decimal(19, 2) DEFAULT NULL,
    account_number  int(11) NOT NULL,
    PRIMARY KEY (id)
) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8;
```

```sql
LOCK TABLES savings_account WRITE;
INSERT INTO savings_account
VALUES (1, 4250.00, 11223147),
       (2, 0.00, 11223151);
UNLOCK TABLES;
```

```sql
DROP TABLE IF EXISTS user;
CREATE TABLE user
(
    user_id            bigint(20) NOT NULL AUTO_INCREMENT,
    email              varchar(255) NOT NULL,
    enabled            bit(1)       NOT NULL,
    first_name         varchar(255) DEFAULT NULL,
    last_name          varchar(255) DEFAULT NULL,
    password           varchar(255) DEFAULT NULL,
    phone              varchar(255) DEFAULT NULL,
    username           varchar(255) DEFAULT NULL,
    primary_account_id bigint(20) DEFAULT NULL,
    savings_account_id bigint(20) DEFAULT NULL,
    PRIMARY KEY (user_id),
    UNIQUE KEY UK_ob8kqyqqgmefl0aco34akdtpe (email),
    KEY                FKbj0uoj9i40dory8w4t5ojyb9n(primary_account_id),
    KEY                FKihums7d3g5cv9ehminfs1539e(savings_account_id),
    CONSTRAINT FKbj0uoj9i40dory8w4t5ojyb9n FOREIGN KEY (primary_account_id) REFERENCES primary_account (id),
    CONSTRAINT FKihums7d3g5cv9ehminfs1539e FOREIGN KEY (savings_account_id) REFERENCES savings_account (id)
) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8;
```

```sql
LOCK TABLES USER WRITE;
INSERT INTO user
VALUES (1, 'uzumaki_naruto@konohagakure.co.jp', '', 'Uzumaki', 'Naruto',
        '$2a$12$DWCryEwHwbTYCegib92tk.VST.GG1i2WAqfaSwyMdxX0cl0eBeSve', '5551112345', 'User', 1, 1),
       (2, 'uchiha_sasuke@konohagakure.co.jp', '', 'Uchiha', 'Sasuke',
        '$2a$12$hZR7pcSf0JU/OTXR3TOyuu8r6C6n.JZE8Ei47E4LZs1t0Aq1AO6oC',
        '1111111111', 'Admin', 2, 2);
UNLOCK TABLES;
```

```sql
DROP TABLE IF EXISTS appointment;
CREATE TABLE appointment
(
    id          bigint(20) NOT NULL AUTO_INCREMENT,
    confirmed   bit(1) NOT NULL,
    date        datetime     DEFAULT NULL,
    description varchar(255) DEFAULT NULL,
    location    varchar(255) DEFAULT NULL,
    user_id     bigint(20) DEFAULT NULL,
    PRIMARY KEY (id),
    INDEX       appointment_id_idx(user_id)
) ENGINE = InnoDB
  AUTO_INCREMENT = 4
  DEFAULT CHARSET = utf8;

ALTER TABLE appointment
    ADD CONSTRAINT user_id
        FOREIGN KEY (user_id) REFERENCES user (user_id)
            ON UPDATE CASCADE ON DELETE CASCADE;
```

```sql
LOCK TABLES appointment WRITE;
INSERT INTO appointment
VALUES (1, '', '2017-01-25 14:01:00', 'Want to see someone', 'Indonesia', 1),
       (2, '\0', '2017-01-30 15:01:00', 'Take credit', 'Indonesia', 1),
       (3, '', '2017-02-16 15:02:00', 'Consultation', 'Indonesia', 1);
UNLOCK TABLES;
```


```sql
DROP TABLE IF EXISTS primary_transaction;
CREATE TABLE primary_transaction
(
    id                 bigint(20) NOT NULL AUTO_INCREMENT,
    amount             double NOT NULL,
    available_balance  decimal(19, 2) DEFAULT NULL,
    date               datetime       DEFAULT NULL,
    description        varchar(255)   DEFAULT NULL,
    status             varchar(255)   DEFAULT NULL,
    type               varchar(255)   DEFAULT NULL,
    primary_account_id bigint(20) DEFAULT NULL,
    PRIMARY KEY (id),
    KEY                FK643wtfdx6y0e093wlc09csehn(primary_account_id),
    CONSTRAINT FK643wtfdx6y0e093wlc09csehn FOREIGN KEY (primary_account_id) REFERENCES primary_account (id)
) ENGINE=InnoDB AUTO_INCREMENT=9 DEFAULT CHARSET=utf8;
```

```sql
LOCK TABLES primary_transaction WRITE;
INSERT INTO primary_transaction
VALUES (1, 5000, 5000.00, '2017-01-13 00:57:16', 'Deposit to Primary Account', 'Finished', 'Account', 1),
       (2, 1500, 3500.00, '2017-01-13 00:57:31', 'Withdraw from Primary Account', 'Finished', 'Account', 1),
       (3, 1300, 2200.00, '2017-01-13 00:58:03', 'Between account transfer from Primary to Savings', 'Finished',
        'Account', 1),
       (4, 500, 1700.00, '2017-01-13 00:59:08', 'Transfer to recipient Mr. Tomson', 'Finished', 'Transfer', 1),
       (5, 1500, 3200.00, '2017-01-13 01:11:38', 'Deposit to Primary Account', 'Finished', 'Account', 1),
       (6, 400, 2800.00, '2017-01-13 01:11:46', 'Withdraw from Primary Account', 'Finished', 'Account', 1),
       (7, 2300, 2000.00, '2017-01-13 01:13:48', 'Between account transfer from Primary to Savings', 'Finished',
        'Account', 1),
       (8, 300, 1700.00, '2017-01-13 01:14:14', 'Transfer to recipient TaxSystem', 'Finished', 'Transfer', 1);
UNLOCK TABLES;
```


```sql
DROP TABLE IF EXISTS recipient;
CREATE TABLE recipient
(
    id             bigint(20) NOT NULL AUTO_INCREMENT,
    account_number varchar(255) DEFAULT NULL,
    description    varchar(255) DEFAULT NULL,
    email          varchar(255) DEFAULT NULL,
    name           varchar(255) DEFAULT NULL,
    phone          varchar(255) DEFAULT NULL,
    user_id        bigint(20) DEFAULT NULL,
    PRIMARY KEY (id),
    KEY            FK3041ks22uyyuuw441k5671ah9(user_id),
    CONSTRAINT FK3041ks22uyyuuw441k5671ah9 FOREIGN KEY (user_id) REFERENCES user (user_id)
) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=utf8;
```

```sql
LOCK TABLES recipient WRITE;
INSERT INTO recipient
VALUES (1, '213425635454', 'Rent payment', 'tomson@gmail.com', 'Mr. Tomson', '1112223333', 1),
       (2, '453452341324', 'Gym payment', 'fitness@gmail.com', 'LtdFitness', '323245345', 1),
       (3, '5465464234542', 'Tax payment 20%', 'taxes@mail.fi', 'TaxSystem', '34254353', 1);
UNLOCK TABLES;
```


```sql
DROP TABLE IF EXISTS role;
CREATE TABLE role
(
    role_id int(11) NOT NULL,
    name    varchar(255) DEFAULT NULL,
    PRIMARY KEY (role_id)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

```sql
LOCK TABLES ROLE WRITE;
INSERT INTO role
VALUES (0, 'ROLE_USER'),
       (1, 'ROLE_ADMIN');
UNLOCK TABLES;
```


```sql
DROP TABLE IF EXISTS savings_transaction;
CREATE TABLE savings_transaction
(
    id                 bigint(20) NOT NULL AUTO_INCREMENT,
    amount             double NOT NULL,
    available_balance  decimal(19, 2) DEFAULT NULL,
    date               datetime       DEFAULT NULL,
    description        varchar(255)   DEFAULT NULL,
    status             varchar(255)   DEFAULT NULL,
    type               varchar(255)   DEFAULT NULL,
    savings_account_id bigint(20) DEFAULT NULL,
    PRIMARY KEY (id),
    KEY                FK4bt1l2090882974glyn79q2s9(savings_account_id),
    CONSTRAINT FK4bt1l2090882974glyn79q2s9 FOREIGN KEY (savings_account_id) REFERENCES savings_account (id)
) ENGINE=InnoDB AUTO_INCREMENT=7 DEFAULT CHARSET=utf8;
```

```sql
LOCK TABLES savings_transaction WRITE;
INSERT INTO savings_transaction
VALUES (1, 1000, 1000.00, '2017-01-13 00:57:40', 'Deposit to savings Account', 'Finished', 'Account', 1),
       (2, 150, 2150.00, '2017-01-13 01:11:15', 'Withdraw from savings Account', 'Finished', 'Account', 1),
       (3, 400, 1750.00, '2017-01-13 01:11:23', 'Withdraw from savings Account', 'Finished', 'Account', 1),
       (4, 2000, 3750.00, '2017-01-13 01:11:30', 'Deposit to savings Account', 'Finished', 'Account', 1),
       (5, 1500, 2250.00, '2017-01-13 01:13:38', 'Between account transfer from Savings to Primary', 'Finished',
        'Transfer', 1),
       (6, 300, 4250.00, '2017-01-13 01:14:02', 'Transfer to recipient LtdFitness', 'Finished', 'Transfer', 1);
UNLOCK TABLES;
```


```sql
DROP TABLE IF EXISTS user_role;
CREATE TABLE user_role
(
    user_role_id bigint(20) NOT NULL AUTO_INCREMENT,
    role_id      int(11) DEFAULT NULL,
    user_id      bigint(20) DEFAULT NULL,
    PRIMARY KEY (user_role_id),
    KEY          FKa68196081fvovjhkek5m97n3y(role_id),
    KEY          FK859n2jvi8ivhui0rl0esws6o(user_id),
    CONSTRAINT FK859n2jvi8ivhui0rl0esws6o FOREIGN KEY (user_id) REFERENCES user (user_id),
    CONSTRAINT FKa68196081fvovjhkek5m97n3y FOREIGN KEY (role_id) REFERENCES role (role_id)
) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8;
```

```sql
LOCK TABLES user_role WRITE;
INSERT INTO user_role
VALUES (1, 0, 1),
       (2, 1, 2);
UNLOCK TABLES;
```