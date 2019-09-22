# Praktikum Teknologi Cloud
## Pertemuan ke-02

###  Abdul Rohman Wahid / 175410100
--------------------------------    

Pergi ke [Langkah sebelumnya](../minggu-01/README.md)

### Langkah 03 Mengelola Repo
#### Membuat Branch
![BuatBranch](./img/01.png)
Membuat branch sekaligus berpindah ke branch yang baru dibuat dengan perintah :
```
git checkout -b edit-minggu-01
```

#### Melakukan perubahan di Branch
Mengedit file maupun menambahkan file baru saat branch aktif adalah `edit-minggu-01`. Perubahan di simpan seperti biasa dengan `git add` dan `git commit` serta `git push` untuk mempublikasikannya.

#### Melihat hasil perubahan di Branch
![PerubahanBranch](./img/02.png)
Diatas adalah daftar perubahan yang telah terjadi di branch `edit-minggu-01` yang di cek menggunakan perintah 
```
git log
```

#### Kembali ke branch master
![KembaliBranch](./img/03.png)
Kembali ke brach master dengan perintan `git checkout` tanpa menggunakan `-b` yaitu :
```
git checkout master
```