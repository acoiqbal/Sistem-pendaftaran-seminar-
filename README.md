## <p align="center" style="margin-top: 0;">SISTEM PENDAFTARAN SEMINAR</p>
<p align="center">
  <img src="LOGO-UNSULBAR.png" width="300" alt="Deskripsi gambar" />
</p>

### <p align="center">ACO IQBAL </p>
### <p align="center">D0223041</p></br>
### <p align="center">Framework Web Based</p>
### <p align="center">2025</p>

---
## Role dan Fitur
### 1. Admin
| Fitur | 
| ----------- | 
| Kelola data seminar (Create, Read, Update, Delete) | 
| Melihat semua pendaftaran peserta | 
| Akses dashboard admin | 

### 2. Panitia 
| Fitur | 
| ----------- |
| Melihat daftar pendaftar seminar |
| Menerima atau menolak pendaftaran peserta (accepted / rejected) | 
| Akses dashboard panitia | 

### 3. Peserta 
| Fitur |
| ----------- |
| Melihat daftar seminar yang tersedia | 
| Mendaftar seminar jika kuota masih ada | 
| Melihat status pendaftaran (pending/accepted/rejected) | 
|Akses dashboard peserta|

---
## Tabel-tabel database beserta field dan tipe datanya

### 1. Tabel ```{users}```
| Field | Tipe Data | Keterangan |
| ----------- | ----------- | ----------- |
| id | INT(PK) | Primary Key |
| nama | VARCHAR(100) | Nama User |
| role_id | INT(FK) | Relasi ke ```{roles.id}``` |
| email | VARCHAR(100) | Email Unik |
| password | VARCHAR(255) | Password |
| created_at | TIMESTAMP | Waktu dibuat |
| updated_at | TIMESTAMP | Waktu diupdate |

### 2. Tabel ```{roles}```
| Field | Tipe Data | Keterangan |
| ----------- | ----------- | ----------- |
| id | INT(PK) | Primary Key |
| nama | VARCHAR(100) | Nama Role: admin, panitia, peserta  |
| created_at | TIMESTAMP | Waktu dibuat |

### 3. Tabel ```{seminar}```
| Field | Tipe Data | Keterangan |
| ----------- | ----------- | ----------- |
| id | INT(PK) | Primary Key |
| judul | VARCHAR(100) | judul seminar |
| deskripsi | TEXT | deskripsi seminar  |
| lokasi | VARCHAR (255) | lokasi seminar |
| date | DATETIME | tanggal dan waktu |
| kapasitas | INT(15) | kapasitas seminar |
| created_at | TIMESTAMP | Waktu dibuat |
| updated_at | TIMESTAMP | Waktu diupdate |

### 4. Tabel ```{registrasions}```
| Field | Tipe Data | Keterangan |
| ----------- | ----------- | ----------- |
| id | INT(PK) | Primary Key |
| user_id | BIGINT | Foreign Key ke users(id) |
| seminar_id | BIGINT | Foreign Key ke seminars(id) |
| status | ENUM | 'pending', 'accepted', 'rejected' |
| created_at | TIMESTAMP | Waktu dibuat |
| updated_at | TIMESTAMP | Waktu diupdate |

---
## Jenis relasi dan tabel yang berelasi
| Tabel Asal | Tabel Tujuan | Jenis Relasi | Keterangan |
| ----------- | ----------- | ----------- | ----------- |
| ```users.role_id``` | ```roles.id``` | Many to One | Banyak user bisa punya satu role |
| ```registrasions.user_id``` | ```users.id``` | One to Many | Satu user (peserta) bisa mendaftar ke banyak seminar |
| ```registrasions.seminar_id``` | ```seminar.id``` | One to Many | Satu seminar bisa diikuti oleh banyak peserta.Satu pendaftaran hanya untuk satu seminar. |
