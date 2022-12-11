# NAMA      : ZIDNA SOLEDA ZULFA
# KELAS     : TI.22.B1

#                             LATIHAN OOP PADA PYTHON DENGAN MENGAPLIKASIKAN PENGGUNAAN CLASS

1. Flowchart program yang akan kita buat

![image](https://user-images.githubusercontent.com/115474076/206900031-a483f2da-cb5d-4f76-982f-7812385e254f.png)


2. Masukan coding di bawah ini dan run di terminal python

          # import tabulate
          from tabulate import tabulate

          # Zidna Soleda Zulfa
          #TI.22.B1

          # Membuat class dengan nama Mahasiswa

          class Mahasiswa:
              def __init__(self):
                  #   Membuat properti dataMahasiswa bertipe dictionary
                  self.dataMahasiswa = {
                      'No'            : [],
                      'Nim'           : [],
                      'Nama'          : [],
                      'Tugas'         : [],
                      'UTS'           : [],
                      'UAS'           : [],
                      'Nilai Akhir'   : [],
                  }

          # method untuk menampilkan data
          # self merupakan parameter untuk mengakses properti

              def tampilkan(self):
                  print("Berikut data yang ada")
                  print(tabulate(self.dataMahasiswa, headers =[
                      'No', 'Nim', 'Nama', 'Tugas', 'UTS', 'UAS', 'Nilai Akhir'], tablefmt="fancy_grid"))

          # method untuk menambahkan data

              def tambah(self, no):
                  # menginput data
                  Nim = int(input("Masukan NIM            : "))
                  Nama = input("Masukan Nama           : ")
                  Tugas = int(input("Masukan Nilai Tugas    : "))
                  UTS = int(input("Masukan Nilai UTS      : "))
                  UAS = int(input("Masukan Nilai UAS      : "))
                  Nilai_Akhir = (Tugas * 30/100) + (UTS *35/100) + (UAS * 35/100)
                  # menambahkan data
                  self.dataMahasiswa['No'].append(no)
                  self.dataMahasiswa['Nim'].append(Nim)
                  self.dataMahasiswa['Nama'].append(Nama)
                  self.dataMahasiswa['UTS'].append(UTS)
                  self.dataMahasiswa['UAS'].append(UAS)
                  self.dataMahasiswa['Tugas'].append(Tugas)
                  self.dataMahasiswa['Nilai Akhir'].append(Nilai_Akhir)
                  print('Data berhasil ditambahkan.')
              # print(tabulate(dataMahasiswa, headers=[
              #       'NIM', 'Nama', 'Tugas', 'UTS', 'UAS', 'Nilai Akhir'], tablefmt="fancy_grid"))

          # method untuk mengedit data

              def ubah(self, Nama):
                  # cek jika ada nama tersebut di dataMahasiswa
                  if Nama in self.dataMahasiswa['Nama']:
                      # cari posisi indexnya lalu disimpan di nimIndex
                      namaIndex = self.dataMahasiswa['Nama'].index(Nama)
                      print("Pilih data yang mau di edit : ")
                  # peruntungan mengedit data dalam bentuk pilihan
                  while True:
                      editApa = int(input(
                          "(1) Nim, \n (2) Nama, \n (3) Nilai Tugas, \n (4) Nilai UTS, \n (5) Nilai UAS, \n (0) Save perubahan dan exit, \n "))
                      print(" ")

                      if editApa == 1:
                          # merubah Nim
                          newNim = int(input("Masukan Nim : "))
                          self.dataMahasiswa['NIM'][namaIndex] = newNim
                      elif editApa == 2:
                          # merubah Nama
                          newNama = input("Masukan Nama : ")
                          self.dataMahasiswa['Nama'][namaIndex] = newNama
                      elif editApa == 3:
                          # merubah Nilai Tugas & Nilai Akhir
                          newTugas = int(input("Masukan Nilai Tugas : "))
                          nilai_akhir = (newTugas * 30/100) + (self.dataMahasiswa['UTS'][namaIndex] * 35/100) + (
                              self.dataMahasiswa['UAS'][namaIndex] * 35/100)
                          self.dataMahasiswa['Tugas'][namaIndex] = newTugas
                          self.dataMahasiswa['Nilai Akhir'][namaIndex] = nilai_akhir
                      elif editApa == 4:
                          # merubah nilai UTS & Nilai Akhir
                          newUTS = int(input("Masukan Nilai UTS"))
                          nilai_akhir = (self.dataMahasiswa['Tuga'][namaIndex] * 30/100) + (newUTS *35/100) + (self.dataMahasiswa['UAS'][namaIndex] * 35/100)
                          self.dataMahasiswa['UTS'][namaIndex] = newUTS
                          self.dataMahasiswa['Nilai Akhir'][namaIndex] = nilai_akhir
                      elif editApa == 5:
                          # merubah nilai UAS & nilai akhir
                          newUAS = int(input("Masukn Nilai UAS : "))
                          nilai_akhir = (self.dataMahasiswa['Tugas'][namaIndex] * 30 / 100) + (self.dataMahasiswa['UTS'][namaIndex] * 35 / 100) + (newUAS * 35 / 100)
                          self.dataMahasiswa['UAS'][namaIndex] = newUAS
                          self.dataMahasiswa['Nilai Akhir'][namaIndex]= nilai_akhir
                      elif editApa == 0:
                          print("Perubahan data berhasil di simpan")
                          break
                  else:
                      print("Data tidak ditemukan")

          # fungsi untuk menghapus data

              def hapus(self, nama):
                  if nama in self.dataMahasiswa['Nama']:
                      namaIndex = self.dataMahasiswa['Nama'].index(nama)
                      # menghapus data berdasasrkan position index pada nama
                      del self.dataMahasiswa['No'][namaIndex]
                      del self.dataMahasiswa['Nim'][namaIndex]
                      del self.dataMahasiswa['Nama'][namaIndex]
                      del self.dataMahasiswa['Tugas'][namaIndex]
                      del self.dataMahasiswa['UTS'][namaIndex]
                      del self.dataMahasiswa['UAS'][namaIndex]
                      del self.dataMahasiswa['Nilai Akhir'][namaIndex]
                      print("Data berhasil di hapus. ")
                  else:
                      print("Data tidak ditemukan")

          # fungsi untuk mencari data

          # melakukan perulangan menggunkan while sampai user menekan huruf Q perulangan akan
          no = 0
          # instansiassi class mahasiswa dengan nama instanceMhs
          instanceMhs = Mahasiswa()

          # melakukan perulangan sampai kondisi tertentu terpenuhi perulangan akan berhenti
          while True:
              # opsi input pilihan T,L,U,H,C,K
              tanya = input (
                  " (T) Menambah Data \n (L) Melihat Semua Data \n (U) Update Data \n (H) Menghapus Data \n (C) Mencari Data \n (K) Keluar Program : ") 
              if tanya == "T":
                  # Melakukan perulangan hingga user memilih n maka perulangan akan berhenti
                  while True:
                      no += 1
                      # memanggil fungsi tambahData dan memparsing data no
                      instanceMhs.tambah(no)
                      tambahDataLagi = input("Tambah data lagi ? (y/n) : ")
                      if tambahDataLagi == 'n':
                          break
                  # jika tanya == L maka melihat data
              elif tanya == "L":
                  # menampilkan data dalam bentuk table menggunkan package tablate
                  instanceMhs.tampilkan()
                  print(" ")
                  # jika tanya == U maka mengedit data
              elif tanya == "U":
                  print(tabulate(instanceMhs.dataMahasiswa, headers=[ 
                      'No', 'Nim', 'Nama', 'Tugas', 'UTS', 'UAS', 'Nilai Akhir'], tablefmt="fancy_grid"))
                  nama = input('Masukan Nama yang mau di edit : ')
                  print(" ")
                  instanceMhs.ubah(nama)
                  # jika tanya == H maka Hapus data
              elif tanya == "H":
                  print(tabulate(instanceMhs.dataMahasiswa, headers=[
                      'No', 'Nim', 'Nama', 'Tugas', 'UTS', 'UAS', 'Nilai Akhir'], tablefmt="fancy_grid"))
                  nama = input('Masukan Nama yang mau di hapus :')
                  print(" ")
                  instanceMhs.hapus(nama)
                  # jika tanya == K maka keluar dari program
              elif tanya == "K":
                  print(" ")
                  print("Anda telah keluar dari program.")
                  print("Terimakasih.")
                  break
                  
 3. Hasil outputnya
 
 - jika memilih opsi tambah data ketik T
 
 ![image](https://user-images.githubusercontent.com/115474076/206900244-796e7f22-d9eb-4be0-87ff-29577a11d34d.png)


- jika ingin melihat data ketik L

![image](https://user-images.githubusercontent.com/115474076/206900277-3e902982-51c9-4f0f-ab37-093356a5979f.png)

- jika ingin mengedit data dan save perubahan ketik U dan

![image](https://user-images.githubusercontent.com/115474076/206900365-9d631fa5-e028-45f3-898e-addcbfd73985.png)


- untuk menghapus data ketik H

![image](https://user-images.githubusercontent.com/115474076/206900508-e7cfb3ae-343a-40e9-bb74-68676b1f76b7.png)


- untuk keluar dari program ketik K

![image](https://user-images.githubusercontent.com/115474076/206900524-5e9ea193-47d1-4a79-bd55-cd654e48790e.png)


