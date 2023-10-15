# Postest2
Nama:Fadhil Ahmad Khairan
Kelas:Sistem Informasi B
NIM:2309116071
![Screenshot 2023-10-09 232931](https://github.com/Fadhilllak/Postest2/assets/146011121/afd47af1-509c-486d-8392-3bd265bda45b)
Ini adalah tampilan awal pada tema saya yaitu toko alat lukis,di situ ada pilihan untuk memilih menu admin menu costumer,dan keluar
![Screenshot 2023-10-09 232952](https://github.com/Fadhilllak/Postest2/assets/146011121/56989419-6c4f-41b2-9ae5-8f9d9be664a8)
Kemudian kita memilih Pilihan pertama yaitu pilihan menu admin,kita harus memasukan password terlebih dahulu Nama:rinnmoka password:12345
![Screenshot 2023-10-09 233005](https://github.com/Fadhilllak/Postest2/assets/146011121/629ed232-e706-45d9-b3b3-67db0660a86d)
Di menu admin kita ada tersedia sekitar 5 pilihan yaitu tambah alat,tampilkan semua alat,update alat,,hapus alat,dan kembali ke menu utama
![Screenshot 2023-10-09 233025](https://github.com/Fadhilllak/Postest2/assets/146011121/62d8f719-81f5-48c7-b5ce-118e5741d90c)
kemudian kita login sebagai costumer(pembeli)
![Screenshot 2023-10-09 233039](https://github.com/Fadhilllak/Postest2/assets/146011121/6883c3cb-fc90-45a9-80c9-08626208d1b5)
Di menu pembeli tersedia lihat daftar alat,beli alat dan kembali ke halaman utama
![Screenshot 2023-10-09 233054](https://github.com/Fadhilllak/Postest2/assets/146011121/da883256-e83d-4a4b-aa3c-778824f5de8f)
Ini adalah list nama nama alat di toko alat lukis
![Screenshot 2023-10-09 233112](https://github.com/Fadhilllak/Postest2/assets/146011121/76200c43-70ea-4089-8389-ffa38e27ae00)
kemudian kita pilih alat yang mau kita pilih
![Screenshot 2023-10-09 233112](https://github.com/Fadhilllak/Postest2/assets/146011121/4a084a41-9be8-4316-9614-bd1e7ed706d2)
Ini adalah struk dari pembelian barang dengan harga
![Screenshot 2023-10-09 233127](https://github.com/Fadhilllak/Postest2/assets/146011121/24d3b9af-9ed9-4c81-b79a-dfdc2319bdce)
Kemudian kita kembali ke menu awal 
![Screenshot 2023-10-09 233137](https://github.com/Fadhilllak/Postest2/assets/146011121/dd69ef91-ee04-4114-9dc2-0d3aafc2a808)
dan semuanya selesai,begitu isi dari codingan toko alat lukis
berikut ini adalah flowchartnya
![Screenshot 2023-10-09 232911](https://github.com/Fadhilllak/Postest2/assets/146011121/0d765a01-35ca-4cc9-88cb-0373a03a0a2b)

berikut adalah codingan nya

import os
from prettytable import PrettyTable

# List untuk menyimpan data alat lukis
alat_lukis = []
id_terakhir = 0

# Data awal (5 alat lukis)
data_awal = [
    {"nama": "Kuas", "harga": 5000.0, "stok": 8},
    {"nama": "Pensil", "harga": 2000.0, "stok": 4},
    {"nama": "Spidol", "harga": 8000.0, "stok": 7},
    {"nama": "Cat Air", "harga": 25000.0, "stok": 5},
    {"nama": "Kanvas", "harga": 75000.0, "stok": 3}
]

for data in data_awal:
    id_terakhir += 1
    alat = {
        'id': id_terakhir,
        'nama': data['nama'],
        'harga': data['harga'],
        'stok': data['stok']
    }
    alat_lukis.append(alat)


# Data username dan password
data_admin = {
    'username': 'rinnmoka',
    'password': '12345'
}

data_user = {
    'username': 'user',
    'password': 'user123'
}

def clear_screen():
    os.system('cls' if os.name == 'nt' else 'clear')

def login(role):
    if role == 'admin':
        data = data_admin
    else:
        data = data_user

    username = input(f"Masukkan username {role}: ")
    password = input(f"Masukkan password {role}: ")

    if username == data['username'] and password == data['password']:
        return True
    else:
        return False

def tambah_alat():
    global id_terakhir
    id_terakhir += 1
    nama = input("Masukkan nama alat: ")
    harga = float(input("Masukkan harga alat: "))
    stok = int(input("Masukkan stok alat: "))
    
    alat = {
        'id': id_terakhir,
        'nama': nama,
        'harga': harga,
        'stok': stok
    }
    alat_lukis.append(alat)
    print(f"Alat {nama} berhasil ditambahkan!")

def tampilkan_alat():
    table = PrettyTable()
    table.field_names = ["ID", "Nama", "Harga", "Stok"]
    for alat in alat_lukis:
        table.add_row([alat['id'], alat['nama'], alat['harga'], alat['stok']])
    print(table)


def update_alat():
    tampilkan_alat()
    id = int(input("Masukkan ID alat yang ingin diupdate: "))
    for alat in alat_lukis:
        if alat['id'] == id:
            alat['nama'] = input("Masukkan nama alat baru: ")
            alat['harga'] = float(input("Masukkan harga alat baru: "))
            alat['stok'] = int(input("Masukkan stok alat baru: "))
            print(f"Alat dengan ID {id} berhasil diupdate!")
            return
    print(f"Alat dengan ID {id} tidak ditemukan!")

def hapus_alat():
    tampilkan_alat()
    id = int(input("Masukkan ID alat yang ingin dihapus: "))
    for alat in alat_lukis:
        if alat['id'] == id:
            alat_lukis.remove(alat)
            print(f"Alat dengan ID {id} berhasil dihapus!")
            return
    print(f"Alat dengan ID {id} tidak ditemukan!")

def beli_alat():
    tampilkan_alat()
    try:
        id = int(input("Masukkan ID alat yang ingin dibeli: "))
        jumlah = int(input("Masukkan jumlah yang ingin dibeli: "))
    except ValueError:
        print("Mohon masukkan angka yang valid.")
        return

    for alat in alat_lukis:
        if alat['id'] == id:
            if alat['stok'] >= jumlah:
                alat['stok'] -= jumlah
                total_harga = alat['harga'] * jumlah
                
                # Menampilkan struk belanja
                clear_screen()
                print("\nStruk Belanja:")
                struk = PrettyTable()
                struk.field_names = ["Nama Alat", "Harga Satuan", "Jumlah", "Total Harga"]
                struk.add_row([alat['nama'], alat['harga'], jumlah, total_harga])
                print(struk)
                print(f"Total yang harus dibayar: {total_harga}")
                input("\nTekan Enter untuk kembali ke menu pembeli...")
                return
            else:
                print(f"Maaf, stok {alat['nama']} tidak mencukupi.")
                input("Tekan Enter untuk kembali ke menu pembeli...")
                return
    print(f"Alat dengan ID {id} tidak ditemukan!")
    input("Tekan Enter untuk kembali ke menu pembeli...")

def menu_admin():
    while True:
        clear_screen()
        print("\nMenu Admin:")
        print("1. Tambah Alat")
        print("2. Tampilkan Semua Alat")
        print("3. Update Alat")
        print("4. Hapus Alat")
        print("5. Kembali ke Menu Utama")
        
        pilihan = input("Pilih menu: ")
        
        if pilihan == "1":
            tambah_alat()
        elif pilihan == "2":
            tampilkan_alat()
            input("Tekan Enter untuk kembali ke menu admin...")
        elif pilihan == "3":
            update_alat()
        elif pilihan == "4":
            hapus_alat()
        elif pilihan == "5":
            break
        else:
            print("Pilihan tidak valid!")
            input("Tekan Enter untuk melanjutkan...")

def menu_pembeli():
    while True:
        clear_screen()
        print("\nMenu Pembeli:")
        print("1. Lihat Daftar Alat Lukis")
        print("2. Beli Alat Lukis")
        print("3. Kembali ke Menu Utama")
        
        pilihan = input("Pilih menu: ")
        
        if pilihan == "1":
            tampilkan_alat()
            input("Tekan Enter untuk kembali ke menu pembeli...")
        elif pilihan == "2":
            beli_alat()
        elif pilihan == "3":
            break
        else:
            print("Pilihan tidak valid!")
            input("Tekan Enter untuk melanjutkan...")

def menu_utama():
    while True:
        clear_screen()
        print("\nMenu Toko Alat Lukis:")
        print("1. Menu Admin")
        print("2. Menu Pembeli")
        print("3. Keluar")
        
        pilihan = input("Pilih menu: ")
        
        if pilihan == "1":
            if login('admin'):
                menu_admin()
            else:
                print("Username atau password admin salah!")
                input("Tekan Enter untuk melanjutkan...")
        elif pilihan == "2":
            if login('user'):
                menu_pembeli()
            else:
                print("Username atau password user salah!")
                input("Tekan Enter untuk melanjutkan...")
        elif pilihan == "3":
            print("Terima kasih!")
            break
        else:
            print("Pilihan tidak valid!")
            input("Tekan Enter untuk melanjutkan...")

if __name__ == "__main__":
    menu_utama()
