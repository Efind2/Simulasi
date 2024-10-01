# Simulasi UTS Mata Kuliah Pemograman Berorientasi Objek
Repository ini adalah repository untuk memenuhi tugas mata kuliah Pemograman Berorientasi Objek(PBO), tujuan repository ini adalah untuk menerapkan **CRUD (Create, Read, Update, Delete)** pada **Java Swing**. Disini saya menggunakan bahasa pemograman java dan menggunakan **IDE NetBeans** sebagai pengembangan program dan saya menggunakan **PostgreSQL** untuk databasenya. Untuk kasusnya saya mengunakan entitas Buku dengan atribut: ISBN, Judul Buku, Tahun Terbit, dan Penerbit.

## Daftar Isi
- [Desain GUI](#desain-gui)
- [Program Tampil](#program-tampil)
- [Program Insert](#program-insert)
- [Program Update](#program-update)
- [Program Delete](#program-delete)
- [Struktur Database](#struktur-database)
## Desain GUI
Untuk membuat desain Gui Swing saya melakukan drag and drop dari fitur yang telah ada di Net Beans, saya menggunakan Text Field sebagai media inputan, Button untuk menjalankan program, dan Table untuk menampilkan data.
![image](https://github.com/user-attachments/assets/5e39a3f0-0525-4d66-ae50-90c2e7652e28)
## Program Tampil
kode dibawah ini untuk menampilkan data di Table

    public void tampil() {
    
        try {
            // TODO code application logi
            Class.forName(driver);
            String sql = "SELECT * FROM buku";
            conn = DriverManager.getConnection(koneksi, user, password);
            stmt = conn.createStatement();

            while (!conn.isClosed()) {

                ResultSet rs = stmt.executeQuery(sql);
                this.jTable1.setModel(DbUtils.resultSetToTableModel(rs));
                while (rs.next()) {
                    System.out.println(String.valueOf(rs.getObject(1)) + " " + String.valueOf(rs.getObject(2)) + " " + String.valueOf(rs.getObject(3)) + " " + String.valueOf(rs.getObject(4)));
                }
                conn.close();
            }

            stmt.close();

        } catch (ClassNotFoundException ex) {
            Logger.getLogger(Simulasi.class.getName()).log(Level.SEVERE, null, ex);
        } catch (SQLException ex) {
            Logger.getLogger(Simulasi.class.getName()).log(Level.SEVERE, null, ex);
        }

    }
## Program Insert
Kode ini digunakan untuk memasukkan data ke tabel, untuk menjalankannya harus memasukkan data  di setiap kolom input, jika tidak maka akan muncul pop up untuk menggisi kolom input yang masih kosong.
![image](https://github.com/user-attachments/assets/2ca94db6-2e6a-4d57-8928-c3e4ad74b3c2)

## Program Update
kode ini digunakan untuk mengupdate data didalam database, setiap kolom bisa diupdate kecuali kolom yang menjadi primary key
![image](https://github.com/user-attachments/assets/616ce1e0-5553-4084-85c5-38c82a7c74d4)

## Program Delete
kode ini digunakan untuk menghapus satu data yang ada di database.
![image](https://github.com/user-attachments/assets/45ce4794-269f-485c-9ff7-242ec01b998a)

## Struktur Database
Struktur tabel di PostgreSQL adalah sebagai berikut:
- **ISBN** (Primary Key)
- **Judul Buku**
- **Tahun Terbit**
- **Penerbit**
```sql
CREATE TABLE buku (
    isbn INTEGER PRIMARY KEY,
    judul_buku VARCHAR(50) NOT NULL,
    tahun_terbit VARCHAR(10) NOT NULL,
    penerbit VARCHAR(50) NOT NULL
);

Semoga Bermanfaat https://emojipedia.org/grinning-face-with-smiling-eyes











