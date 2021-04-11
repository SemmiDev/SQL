**`© 2021 | sammidev `**

# Table of Contents

1. [**`Tugas 3`**](#section-1)
2. [**`UAS DATABASE`**](#section-2)
3. [**`Pratikum 2`**](#pratikum-2)
4. [**`Belajar JOIN`**](#belajar-join)
5. [**`Belajar relation`**](#belajar-relation)

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


































