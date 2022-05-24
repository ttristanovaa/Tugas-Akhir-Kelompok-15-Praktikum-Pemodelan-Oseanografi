# 🔹 **Tugas Akhir Praktikum Pemodelan Oseanografi** 🔹
Repositori ini dibuat untuk memenuhi Tugas Akhir Praktikum Pemodelan Oseanografi. Repositori berisi _script_ pemrograman yang digunakan dalam praktikum yaitu Adveksi-Difusi 1 Dimensi, Adveksi-Difusi 2 Dimensi, Hidrodinamika 1 Dimensi, dan  Model Data Gelombang _National Buoy Data Center_ (NDBC). Bahasa pemrograman yang digunakan adalah _Python_ yang dapat diaplikasikan pada beberapa _platform_ seperti _Google Colaboratory_, _Visual Studio Code_ (VSCODE), dan _Jupyter Notebook_. _Library_ yang digunakan pada kesempatan kali ini adalah _Numpy_, _Matplotlib_, _sys_, dan _Siphon_.

# Kenalan Dulu Yuk! 👋
Kelompok 15 :
1. Anggi Indira Rayhanifa 26050120120012 Oseanografi A
2. Christopher Agung Hutahaean 26050120130088 Oseanografi A
3. Indra Romadhon 26050120140164 Oseanografi B
4. Ismail Basayep 26050120140146 Oseanografi B
5. Muhamad Fadilah Nur Hafid Oseanografi B
6. Nadhifa Az Zahra Oseanografi B
7. Tanya Tristanova 26050120130042 Oseanografi A

***
**_Mandatory Library_ yang diperlukan :**

👩‍💻 _Matplotlib_ (https://pypi.org/project/matplotlib/)
    
_Matplotlib_ adalah _library Python_ yang fokus pada visualisasi data seperti membuat plot grafik. _Matplotlib_ dapat digunakan dalam skrip _Python_, _Python_ dan _IPython shell_, server aplikasi web, dan beberapa _toolkit graphical user interface_ (GUI) lainnya.

👩‍💻 _NumPy_ (https://numpy.org/install/)

_NumPy_ (_Numerical Python_) adalah _library_ _Python_ yang fokus pada _scientific computing_. _NumPy_ memiliki kemampuan untuk membentuk objek N-dimensional array, yang mirip dengan list pada _Python_. Keunggulan _NumPy_ _array_ dibandingkan dengan list pada _Python_ adalah konsumsi memori yang lebih kecil serta runtime yang lebih cepat. NumPy juga memudahkan kita pada Aljabar Linear, terutama operasi pada Vector (1-d _array_) dan Matrix (2-d _array_).

👩‍💻 _sys_ (https://www.codegrepper.com/code-examples/shell/pip+install+sys)

Modul _sys_ digunakan untuk mengakses konfigurasi interpreter pada saat runtime dan berinteraksi dengan environment sistem operasi.

👩‍💻 _Siphon_ (https://unidata.github.io/siphon/latest/installguide.html)

_Siphon_ adalah kumpulan utilitas Python untuk mengunduh data dari layanan data jarak jauh. Dalam kesempatan kali ini data jarak jauh yang digunakan adalah data NDBC.

_Install library_ dilakukan menggunakan miniconda

![WhatsApp Image 2022-05-24 at 19 38 20](https://user-images.githubusercontent.com/105962770/170037069-958f056a-b017-4fc1-aa91-2f3742b7c7c4.jpeg)

***
# 👾 MODUL 1 : Adveksi-Difusi 1 Dimensi
Adveksi  - Difusi merupakan proses transportasi materi dari suatu bagian sistem ke bagian yang lain sebagai hasil dari gerakan molekul acak yang melibatkan proses transportasi fluida dalam bentuk aliran rata – rata atau arus yang dipengaruhi oleh gaya gravitasi atau tekanan dan merupakan gerak horizontal. Model adveksi - difusi dapat ditemukan dalam kehidupan sehari-hari seperti pencemaran sungai maupun kebakaran hutan. Adveksi - difusi merupakan suatu persamaan diferensial parsial. Solusi numerik dari Persamaan adveksi - difusi 1D dapat diselesaikan menggunakan Finite Difference Schemes standar dan non-standar. Metode yang dapat digunakan adalah metode _Backward in Time Central in Space_ (BTCS), metode _Forward in Time Central in Space_ (FTCS) dan terakhir metode Crank-Nicholson. 
> Metode Crank-Nicholson mampu memprediksi hasil yang paling akurat dibanding dengan metode lainnya.

# Persamaan yang digunakan :
* **Persamaan Adveksi Difusi** : Persamaan adveksi-difusi merupakan persamaan yang memuat sifat persamaan adveksi dan persamaa difusi. Persamaan adveksi merupakan suatu persamaan gelombang linear orde satu dan termasuk dalam persamaan diferensial hiperbolik yang menggambarkan mekanisme transportasi suatu gas atau zat cair dengan arah terntentu. Sedangkan persamaan difusi merupakan persamaan diferensial parsial yang merupakan persentasi perpindahan suatu zat dari konsentrasi tinggi ke konsentrasi rendah. Persamaan adveksi-difusi dapat dipahami dalam bentuk persamaan adveksi maupun persamaan difusi.

Persamaan Adeveksi  : ![image](https://user-images.githubusercontent.com/105962770/169956549-b9cf729b-2b25-4f29-93ca-ab3b012f028c.png)
Persamaan Difusi    : ![image](https://user-images.githubusercontent.com/105962770/169956718-6d899167-6010-487e-9416-c185bd008dbe.png)

* **Persamaan Laplace**

![image](https://user-images.githubusercontent.com/105962770/169957106-a69ce4e2-2d1c-4d8b-9822-0d795c623f33.png)

* **Persamaan Metode _Backward in Time Central in Space_ (BTCS)**

![image](https://user-images.githubusercontent.com/105962770/169961236-01999f98-f4a6-4c0d-b85d-38aab798738a.png)

* **Persamaan Metode _Forward in Time Central in Space_ (FTCS)**

![image](https://user-images.githubusercontent.com/105962770/169961366-1be6a05b-b3c1-41cc-b63a-21f22f6b68a4.png)

* **Persamaan Metode Crank-Nicholson**

![image](https://user-images.githubusercontent.com/105962770/169961432-cb94e1d8-34af-49f7-9c84-4fea673e2d6f.png)

***
# 👾 MODUL 2 : Adveksi-Difusi 2 Dimensi
Persamaan Adveksi - Difusi 2 Dimensi sering juga dikenal dengan Persamaan Transportasi dengan berbagai syarat awal dan syarat batas dibahas dengan pendekatan numerik. Adveksi merupakan mekanisme perpindahan massa suatu materi dari satu titik ke titik lainnya. Sedangkan, difusi merupakan mekanisme penyebaran konsentrasi akibat adanya kecepatan aliran dan perbedaan konsentrasi. Persamaan Adveksi - Difusi 2D dapat digambarkan dalam persamaan di bawah ini:

![image](https://user-images.githubusercontent.com/105967038/169849733-06c4e7b0-d644-4002-aef7-2197624fb018.png). 

Penggunaan adveksi - difusi 2 dimensi dapat diterapkan dalam bidang oseanografi, seperti menghitung dan memodelkan persebaran nutrien di laut atau sungai, pemodelan distribusi sedimen, menghitung dan memodelkan penyebaran polutan dari proses industri, mengetahui persebaran polutan dari laguna dengan menghitung input dan outputnya, serta mengetahui sebaran kebocoran minyak di laut.

_Script_ :
```java
import matplotlib.pyplot as plt
import numpy as np
import sys
#%%
def percentage (part, whole):
    percentage = 100 * float(part)/float(whole)
    return str(round(percentage,2)) + 'x'

#Masukan Parameter Awal
C = 0
ad = 1

#Arah Arus
theta = 24
theta = 84
theta = 159
theta = 339

#Parameter Lanjutan
q = 0.95
x = 300
y = 300
dx = 3
dy = 3

#Lama Simulasi
Tend = 102
#Tend = 0,5
dt = 0.5

#Polutan
px = 150
py = 132
Ic = 542

#Perhitungan U dan V
u = C * np.sin(theta*np.pi/180)
v = C * np.cos(theta*np.pi/180)
dt_count = 1/((abs(u)/(q*dx))+(abs(v)/(q*dy))+(2*ad/(q*dx**2))+(2*ad/(q*dy*2)))

Nx = int(x/dx)  #number of mesh in x direction
Ny = int(y/dy)  #number of mesh in y direction
Nt = int(Tend/dt)

#perhitungan titik polutan di buang
px1 = int(px/dx)
py1 = int(py/dy)

#fungsi disederhanakan
lx = u*dt/dx
ly = v*dt/dy
ax = ad*dt/dx**2
ay = ad*dt/dy**2
cfl = (2*ax + 2*ay + abs(lx) + abs(ly))  #syarat kestabilan CFL

#perhitungan cfl
if cfl >= q:
    print('CFL Violated, please use dt :'+str(round(dt_count,4)))
    sys.exit ()

#pembuatan grid 
x_grid = np.linspace(0-dx, x+dx, Nx+2) #ghostnode boundary
y_grid = np.linspace(0-dx, y+dy, Ny+2) #ghostnode boundary
t = np.linspace(0, Tend, Nt+1)
x_mesh, y_mesh = np.meshgrid(x_grid,y_grid)
F = np.zeros((Nt+1, Ny+2, Nx+2))

#kondisi awal
F[0,py1,px1]=Ic

#Iterasi
for n in range (0, Nt):
    for i in range (1,Ny+1):
        for j in range (1, Nx+1):
         F[n+1,i,j]=((F[n,i,j]*(1-abs(lx)-abs(ly))) + \
                (0.5*(F[n,i-1,j]*(ly+abs(ly)))) + \
                (0.5*(F[n,i+1,j]*(abs(ly)-ly))) + \
                (0.5*(F[n,i,j-1]*(lx+abs(lx)))) + \
                (0.5*(F[n,i,j+1]*(abs(lx)-lx))) + \
                (ay*(F[n,i+1,j]-2*(F[n,i,j])+F[n,i-1,j])) +\
                (ax*(F[n,i,j+1]-2*(F[n,i,j])+F[n,i,j-1])))
    #syarat batas
    F[n+1,0,:] = 0 #bc bawah
    F[n+1,:,0] = 0 #bc kiri
    F[n+1,Ny+1,:] = 0 #bc atas
    F[n+1,:,Nx+1] = 0 #bc kanan
    
#Output Gambar
    plt.clf()
    plt.pcolor(x_mesh, y_mesh, F[n+1, :, :], cmap = 'jet',shading='auto',edgecolor='k')
    cbar=plt.colorbar(orientation='vertical',shrink=0.95,extend='both')
    plt.clf()
    plt.pcolor(x_mesh,y_mesh,F[n+1,:,:],cmap='jet',shading='auto',edgecolor='k')
    cbar = plt.colorbar(orientation='vertical',shrink=0.95,extend='both')
    cbar.set_label(label='Concentration',size = 8)
    #plt.clim(0,100)
    plt.title('Kelompok 15_Tugas Kelompok Praktikum Pemodelan Oseanografi \n t='+str(round(dt*(n+1),3))+ ', Initial condition= '+str(Ic),fontsize=10)
    plt.xlabel('x_grid',fontsize=9)
    plt.ylabel('y_grid',fontsize=9)
    plt.axis([0, x, 0, y])
    #plt.pause(0.01)
    plt.savefig(str(n+1)+'.jpg', dpi=300)
    plt.pause(0.01)
    plt.close()
    print('running timestep ke: ' +str(n+1) + ' dari: ' +str(Nt) + '('+ percentage(n+1,Nt)+')')
    print('Nilai CFL:' +str(cfl) + 'dengan arah: ' +str(theta))
```
Parameter berikut dapat diubah sesuai dengan kebutuhan :
```
#Masukan Parameter Awal
C = 0
ad = 1

#Arah Arus
theta = 24
theta = 84
theta = 159
theta = 339

#Parameter Lanjutan
q = 0.95
x = 300
y = 300
dx = 3
dy = 3

#Lama Simulasi
Tend = 102 - Timestamp yang bisa diubah-ubah
#Tend = 0,5
dt = 0.5

#Polutan
px = 150
py = 132
Ic = 542
```

# Hasil _Script_ Adveksi - Difusi 2 Dimensi

* **_Running Timestamp_ 1 dari 204**
 
![image](https://user-images.githubusercontent.com/105962770/170028110-73bb8ee5-70a7-49c4-9c47-ae50f19ce6f2.png)

* **_Running Timestamp_ 102 dari 2014**

![image](https://user-images.githubusercontent.com/105962770/170028233-251938fe-ceb7-446f-8a41-5a0b0fe42980.png)

* **_Running_ _Timestamp_ 204 dari 204**

![image](https://user-images.githubusercontent.com/105962770/170028315-9302fc80-3306-405b-9bb1-628706c30cd5.png)

> Jika timestamp yang diinginkan adalah 204 maka akan ada 204 hasil script, oleh karena itu kami hanya mencantumkan 3 contoh _running script_ modul 2

***
# 👾 MODUL 3 : Hidrodinamika 1 Dimensi
Pada modul 3 dipelajari mengenai persamaan Hidrodinamika 1D. Hidrodinamika adalah ilmu yang mempelajari gerak fluida, khususnya zat cair yang tidak dapat ditekan (_incompressible liquid_) yang dipengaruhi oleh gaya eksternal dan internal. Gaya-gaya yang mempengaruhi pada laut meliputi gaya gravitasi, coriolis, dan sebagainya. Kondisi hidrodinamika merupakan salah satu aspek yang sangat berpengaruh terhadap proses - proses yang terjadi di pantai terutama gelombang dan arus yang bergantung pada bentuk dan karakteristik pantai. Pada praktikum ini persamaan yang digunakan untuk modul hidrodinamika adalah 

**Persamaan Momentum**:

![image](https://user-images.githubusercontent.com/105988579/170135922-d64ef5fe-d2d7-43c3-a034-603607e649f2.png)

**Persamaan Kontinuitas**:

![image](https://user-images.githubusercontent.com/105988579/170135996-bc5e2aba-3040-4e79-98a8-eca941c17543.png)

**Persamaan Transport**

![image](https://user-images.githubusercontent.com/105988579/170137143-dcf52915-a45e-4863-b87e-deee639e2422.png)

**Persamaan Pembangun**

![image](https://user-images.githubusercontent.com/105988579/170137178-6299ad29-928b-48b4-87b8-8175ba2135af.png)

![image](https://user-images.githubusercontent.com/105988579/170137201-e916fd76-b925-4e8f-bc51-81fe700f016f.png)

**Diskretisasi Persamaan**

![image](https://user-images.githubusercontent.com/105988579/170137390-9cf9cc1a-5693-4aae-859a-1f1303246e41.png)

![image](https://user-images.githubusercontent.com/105988579/170137418-f358c0e5-e8b6-45ae-aefb-f32c83f5b1a1.png)

**Penyelesaian Analitik**

![image](https://user-images.githubusercontent.com/105988579/170137541-29424a4f-c14a-4cba-ae50-48328ff6e681.png)

![image](https://user-images.githubusercontent.com/105988579/170137569-a398d37e-9406-4c6c-8469-4a0e142d2dc8.png)


_Script_ :
`'`java
import matplotlib.pyplot as plt
import numpy as np

#Proses Awal
p = 7500        #Panjang Grid
T = 2000        #Waktu Simulasi
A = 0.1         #Amplitudo
D = 5           #Depth/Kedalaman
dt = 2
dx = 100
To = 500        #Periode

#Parameter Lanjutan
g = 9.8          #Koefisien Gravitasi
pi = np.pi 
C = np.sqrt(g*D) #Kecepatan Arus
s = 2*pi/To      #Kecepatan Sudut Gelombang
L = C*To         #Panjang Gelombang
k = 2*pi/L       #Koefisien Panjang Gelombang
Mmax = int(p//dx)
Nmax = int(T//dt)

#Penyelesaian Persamaan Hidrodinamika 1D
zo = [None for _ in range(Mmax)]
uo = [None for _ in range(Mmax)]

hasilu = [None for _ in range(Nmax)]
hasilz = [None for _ in range(Nmax)]

for i in range(1, Mmax+1):
  zo[i-1] = A*np.cos(k*(i)*dx)
  uo[i-1] = A*C*np.cos(k*((i)*dx+(0.5)*dx))/(D+zo[i-1])
for i in range(1, Nmax+1):
  zb = [None for _ in range(Mmax)]
  ub = [None for _ in range(Mmax)]
  zb[0] = A*np.cos(s*(i)*dt)
  ub[-1] = A*C*np.cos(k*L-s*(i)*dt)/(D+zo[-1])
  for j in range (1, Mmax):
    ub[j-1] = uo[j-1]-g*(dt/dx)*(zo[j]-zo[j-1])
  for k in range(2, Mmax+1):
    zb[k-1] = zo[k-1]-(D+zo[k-1])*(dt/dx)*(ub[k-1]-ub[k-2])
    hasilu[i-1] = ub
    hasilz[i-1] = zb
  for p in range(0, Mmax):
    uo[p] = ub[p]
    zo[p] = zb[p]

#Pembuatan Grafik
def rand_col_hex_string():
  return f'#{format(np.random.randint(0,16777215), "#08x")[2:]}'

hasilu_np = np.array(hasilu)
hasilz_np = np.array(hasilz)

fig0, ax0 = plt.subplots(figsize=(12,8))
for i in range (1, 16):
  col0 = rand_col_hex_string()
  line, = ax0.plot(hasilu_np[:,i-1], c=col0, label=f'n={i}')
  ax0.legend()

  ax0.set(xlabel='Waktu', ylabel='Kecepatan Arus', title='''Kelompok 15_Tugas Kelompok Praktikum Pemodelan Oseanografi''')
  ax0.grid()

fig1, ax1 = plt.subplots(figsize=(12,8))
for i in range(1, 16):
  col1= rand_col_hex_string()
  line, = ax1.plot(hasilz_np[:,i-1], c=col1, label=f'n={i}')
  ax1.legend()

  ax1.set(xlabel='Waktu', ylabel='Elevasi Muka Air', 
          title='''Kelompok 15_Tugas Kelompok Praktikum Pemodelan Oseanografi''')
  ax1.grid()

fig2, ax2 = plt.subplots(figsize=(12,8))
for i in range(1, 16):
  col2= rand_col_hex_string()
  line, = ax2.plot(hasilu_np[i-1], c=col2, label=f't={i}')
  ax2.legend()

  ax2.set(xlabel='Grid', ylabel='Kecepatan Arus', 
          title='''Kelompok 15_Tugas Kelompok Praktikum Pemodelan Oseanografi''')
          ax2.grid()

fig3, ax3 = plt.subplots(figsize=(12,8))
for i in range(1, 16):
  col3= rand_col_hex_string()
  line, = ax3.plot(hasilz_np[i-1], c=col3, label=f't={i}')
  ax3.legend()

  ax3.set(xlabel='Grid', ylabel='Elevasi Muka Air', 
          title='''Kelompok 15_Tugas Kelompok Praktikum Pemodelan Oseanografi''')
  ax3.grid()

plt.show()
```

Parameter berikut dapat diubah sesuai dengan kebutuhan :
```
p = 7500        #Panjang Grid
T = 2000        #Waktu Simulasi
A = 0.1         #Amplitudo
D = 5           #Depth/Kedalaman
dt = 2
dx = 100
To = 500        #Periode
```

# Hasil _Script_ Hidrodinamika 1 Dimensi

* **Kecepatan Arus Terhadap Waktu**

![a](https://user-images.githubusercontent.com/105962770/170031416-48e51c44-5b1e-4a6e-8600-edbfb1e0c8a7.png)

* **Elevasi Muka Air Terhadap Waktu**
 
![b](https://user-images.githubusercontent.com/105962770/170031451-04ff3080-76c0-4806-9c01-c50a313ad264.png)

* **Kecepatan Arus Terhadap Grid**

![c](https://user-images.githubusercontent.com/105962770/170031504-6154e9fc-1804-4d65-8d95-ec023a1c5365.png)

* **Elevasi Muka Air Terhadap Grid**

![d](https://user-images.githubusercontent.com/105962770/170031550-29a00ab2-b046-4aad-8927-4bee0b47d64a.png)

***
# 👾 MODUL 4 : Model Data Gelombang _National Buoy Data Center_ (NDBC)
Pada modul 4, kita perlu mengakses hasil pembagian Station_ID sesuai dengan NIM melalui website NDBC-NOAA dan menentukan serta menganalisis letak buoy. _National Data Buoy Center_ (NDBC) adalah bagian dari _National Oceanic and Atmospheric Administration_ (NOAA) _National Weather Service_ (NWS). Gelombang di laut memiliki pergerakan yang acak dan komplek, sehingga tinggi dan periode gelombang sulit untuk diukur dan dirumuskan secara akurat. Teknologi pemantauan gelombang laut telah berkembang selama 40 tahun terakhir. Wahana terapung seperti _wave buoy_ telah digunakan secara luas di seluruh dunia untuk mengukur gelombang permukaan yaitu sebagai referensi atau validasi data ramalan. NDBC merancang, mengembangkan, mengoperasikan, dan memelihara jaringan pelampung pengumpul data dari stasiun yang ada di pesisir. Data parameter yang didapatkan di stasiun NDBC dapat digunakan salah satunya untuk mengetahui transportasi larva ikan pada suatu perairan. Selain itu juga dapat digunakan dalam penentuan daerah penangkapan ikan, penentuan navigasi, rute perjalanan kapal, dan lainnya. Grafik yang dihasilkan dari script modul 4 berupa _Pressure_ [hPa], _Wind Speed_ [m/s] dan _Wind Direction_ [degC].

_Script_ :
```java
import matplotlib.pyplot as plt

from siphon.simplewebservice.ndbc import NDBC

#-------------------------------------------------------------------------------------------#
df = NDBC.realtime_observations('sesuai stasiun yang diinginkan') #Station ID
df.head()

#-------------------------------------------------------------------------------------------#
fig, (ax1, ax2, ax3) = plt.subplots(3, 1, figsize=(12, 10))
ax2b = ax2.twinx()

#Pressure
ax1.plot(df['time'], df['pressure'], color='black')
ax1.set_ylabel('Pressure [hPa]')
fig.suptitle('Kelompok 15_Tugas Kelompok Praktikum Pemodelan Oseanografi', fontsize = 18)

#Wins speed, gust, direction
ax2.plot(df['time'], df['wind_speed'], color='tab:olive')
ax2.plot(df['time'], df['wind_gust'], color='tab:orange', linestyle='--')
ax2b.plot(df['time'], df['wind_direction'], color='tab:blue', linestyle='-')
ax2.set_ylabel('Wind Speed [m/s]')
ax2b.set_ylabel('Wind Direction')

#Water temperature
ax3.plot(df['time'], df['water_temperature'], color='tab:brown')
ax3.set_ylabel('Water Temperature [degC]')

plt.show()
```

> Stasiun yang digunakan pada script dapat dicari pada https://www.ndbc.noaa.gov/
# Salah satu contoh stasiun yang ada pada website noaa yaitu Station 41029 - Capers Nearshore, SC (CAP2)
![41029_mini (1)](https://user-images.githubusercontent.com/106136915/170044725-3b68af72-40a0-4795-bf35-f34184748653.jpg)
# Hasil _Script_ Model Data Gelombang _National Buoy Data Center_ (NDBC)

![image](https://user-images.githubusercontent.com/105962770/169971863-1a24c41e-7b19-4a4a-a1e5-d496011eb1b6.png)
> Hasil dari _running script_ modul 4 dapat berbeda dengan fenomena yang terjadi sebenarnya (karena adanya anomali), anomali tersebut menggambarkan salah satu parameter yang diukur yaitu kecepatan angin, dimana kecepatan angin merupakan salah satu faktor yang mempengaruhi kecepatan arus dan besar gelombang, sehingga station tidak secara langsung mengukur kecepatan arus atau beras gelombang

***
# Demikian Tugas Akhir Kelompok Praktikum Pemodelan Oseanografi ini kami buat, kami meminta maaf jika ada kesalahan dalam penulisan ataupun hasil script yang dibuat. Akhir kata kami ucapkan terima kasih kepada setiap orang yang terlibat dalam pembuatan tugas akhir ini. Byee 👋👽

***
# Tautan
1. Materi Adveksi - Difusi https://www.youtube.com/watch?v=UM0o0ToluY8&ab_channel=CasparHewett
2. Panduan GitHub https://github.com/endymuhardin/buku-pandoc/blob/master/buku/02-markdown.md
3. NDBC https://www.ndbc.noaa.gov/
4. Install Matplotlib https://pypi.org/project/matplotlib/
5. Install NumPy https://numpy.org/install/
6. Install sys https://www.codegrepper.com/code-examples/shell/pip+install+sys
7. Install Siphon https://unidata.github.io/siphon/latest/installguide.html
