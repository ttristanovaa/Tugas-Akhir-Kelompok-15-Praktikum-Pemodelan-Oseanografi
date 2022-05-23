# Tugas Akhir Praktikum Pemodelan Oseanografi
Repositori ini dibuat untuk memenuhi Tugas Akhir Praktikum Pemodelan Oseanografi. Repositori berisi script pemrograman yang digunakan dalam praktikum yaitu Adveksi-Difusi 1 Dimensi, Adveksi-Difusi 2 Dimensi, Hidrodinamika 1 Dimensi, dan  Model Data Gelombang National Buoy Data Center (NDBC). Bahasa pemrograman yang digunakan adalah python yang dapat diaplikasikan pada beberapa platform seperti Google Colaboratory dan Jupyter Notebook. Sedangkan untuk library yang digunakan kali ini adalah Numpy, Matplotlib, dan Siphon.
# Kelompok 15 :
1. Anggi Indira Rayhanifa_26050120120012_Oseanografi A
2. Christopher Agung Hutahaean_26050120130088_Oseanografi A
3. Indra Romadhon_26050120140164_Oseanografi B
4. Ismail Basayep Oseanografi B
5. Muhamad Fadilah Nur Hafid Oseanografi B
6. Nadhifa Az Zahra Oseanografi B
7. Tanya Tristanova_26050120130042 Oseanografi A
# MODUL 1 : Adveksi-Difusi 1 Dimensi
Difusi  - adveksi merupakan proses transportasi materi dari suatu bagian sistem ke bagian yang lain sebagai hasil dari gerakan molekul acak yang melibatkan proses transportasi fluida dalam bentuk aliran rata – rata atau arus yang dipengaruhi oleh gaya gravitasi atau tekanan dan merupakan gerak horizontal. Secara matematis, persamaan difusi-adveksi dapat ditulis sebagai   , u Vu Du t x xx dengan u adalah konsentrasi zat dalam fluida, V adalah kecepatan adveksi, dan D adalah koefisien difusi. Model difusi-adveksi dapat ditemukan dalam kehidupan sehari-hari seperti pencemaran sungai maupun kebakaran hutan. Adveksi - Difusi merupakan suatu persamaan diferensial parsial. Adveksi merupakan mekanisme perpindahan massa suatu materi dari satu titik ke titik lainnya. Sedangkan, difusi merupakan mekanisme penyebaran konsentrasi akibat adanya kecepatan aliran dan perbedaan konsentrasi. GAIS AKU GATAU INI ENAKNYA DIISI APA HE HE HE 
# MODUL 2 : Adveksi-Difusi 2 Dimensi
Persamaan Adveksi - Difusi 2D sering juga dikenal dengan Persamaan Transportasi dengan berbagai syarat awal dan syarat batas dibahas dengan pendekatan numerik. Adveksi merupakan mekanisme perpindahan massa suatu materi dari satu titik ke titik lainnya. Sedangkan, difusi merupakan mekanisme penyebaran konsentrasi akibat adanya kecepatan aliran dan perbedaan konsentrasi. Persamaan Adveksi - Difusi 2D dapat digambarkan dalam persamaan di bawah ini:

![image](https://user-images.githubusercontent.com/105967038/169849733-06c4e7b0-d644-4002-aef7-2197624fb018.png). 

Penggunaan adveksi-difusi 2 dimensi dapat diterapkan dalam bidang oseanografi, seperti menghitung dan memodelkan persebaran nutrien di laut atau sungai, pemodelan distribusi sedimen, menghitung dan memodelkan penyebaran polutan dari proses industri, mengetahui persebaran polutan dari laguna dengan menghitung input dan outputnya, serta mengetahui sebaran kebocoran minyak di laut.


Script:
#!/usr/bin/env python
#coding: utf-8

import matplotlib.pyplot as plt
import numpy as np
import sys

def percentage(part, whole):
    percentage = 100 * float(part)/float(whole)
    return str(round(percentage,2)) + "x"

#Masukan Parameter Awal
C = 0.21
ad = 1.21

#Arah Arus
theta = 21
#theta = 81
#theta = 156
#theta = 336

#Parameter Lanjutan
q = 0.95
x = 300
y = 300
dt = 0.5
dx = 3
dy = 3


#Lama Simulasi
Tend = 102
#Tend = 1
dt = 0.5

#Polutan
px = 150
py = 132
Ic = 512

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
#%%

#pembuatan grid 
x_grid = np.linspace(0-dx, x+dx, Nx+2) #ghostnode boundary
y_grid = np.linspace(0-dx, y+dy, Ny+2) #ghostnode boundary
t = np.linspace(0, Tend, Nt+1)
x_mesh, y_mesh = np.meshgrid(x_grid,y_grid)
F = np.zeros((Nt+1, Ny+2, Nx+2))

#kondisi awal
F[0,py1,px1]=Ic
#%%

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
#%%

    #Output Gambar
    plt.clf()
    plt.pcolor(x_mesh, y_mesh, F[n+1, :, :], cmap = 'jet',shading='auto',edgecolor='k')
    cbar=plt.colorbar(orientation='vertical',shrink=0.95,extend='both')
    plt.clf()
    plt.pcolor(x_mesh,y_mesh,F[n+1,:,:],cmap='jet',shading='auto',edgecolor='k')
    cbar = plt.colorbar(orientation='vertical',shrink=0.95,extend='both')
    cbar.set_label(label='Concentration',size = 8)
    #plt.clim(0,100)
    plt.title('Kelompok 15_Tugas Kelompok Praktikum Pemodelan Oseanografi \n t='+str(round(dt*(n+1),3))+ ', Initial condition='+str(Ic),fontsize=10)
    plt.xlabel('x_grid',fontsize=9)
    plt.ylabel('y_grid',fontsize=9)
    plt.axis([0, x, 0, y])
    #plt.pause(0.01)
    plt.savefig(str(n+1)+'.jpg', dpi=300)
    plt.pause(0.01)
    plt.close()
    print('running timestep ke:' +str(n+1) + ' dari:' +str(Nt) + '('+ percentage(n+1,Nt)+')')
    print('Nilai CFL:' +str(cfl) + 'dengan arah: ' +str(theta))
    
   # Hasil Pemodelan
   
# MODUL 3 : Hidrodinamika 1 Dimensi
Pada modul 3 dipelajari mengenai persamaan Hidrodinamika 1D. Hidrodinamika adalah ilmu yang mempelajari gerak fluida, khususnya zat cair yang tidak dapat ditekan (incompressible liquid) yang dipengaruhi oleh gaya eksternal dan internal. Gaya-gaya yang mempengaruhi pada laut meliputi gaya gravitasi, coriolis, dan sebagainya. Kondisi hidrodinamika merupakan salah satu aspek yang sangat berpengaruh terhadap proses - proses yang terjadi di pantai terutama gelombang dan arus yang bergantung pada bentuk dan karakteristik pantai. Pada praktikum ini persamaan yang digunakan untuk modul hidrodinamika adalah persamaan momentum dan persamaan kontinuitas.

# Hasil Pemodelan Modul 3

# MODUL 4 : Model Data Gelombang National Buoy Data Center (NDBC)
Pada modul 4, kita perlu mengakses hasil pembagian Station_ID sesuai dengan NIM melalui website NDBC-NOAA dan menentukan serta menganalisis letak buoy. _National Data Buoy Center_ (NDBC) adalah bagian dari _National Oceanic and Atmospheric Administration_ (NOAA) _National Weather Service_ (NWS). Gelombang di laut memiliki pergerakan yang acak dan komplek, sehingga tinggi dan periode gelombang sulit untuk diukur dan dirumuskan secara akurat. Teknologi pemantauan gelombang laut telah berkembang selama 40 tahun terakhir. Wahana terapung seperti wave buoy telah digunakan secara luas di seluruh dunia untuk mengukur gelombang permukaan yaitu sebagai referensi atau validasi data ramalan. NDBC merancang, mengembangkan, mengoperasikan, dan memelihara jaringan pelampung pengumpul data dari stasiun yang ada di pesisir. Data parameter yang didapatkan di stasiun NDBC dapat digunakan salah satunya untuk mengetahui transportasi larva ikan pada suatu perairan. Selain itu juga dapat digunakan dalam penentuan daerah penangkapan ikan, penentuan navigasi, rute perjalanan kapal, dan lainnya. Grafik yang dihasilkan dari script modul 4 berupa Pressure [hPa], Wind Speed [m/s] dan Wind Direction [degC].


# Hasil Pemodelan Modul 4
![image](https://user-images.githubusercontent.com/105967038/169859582-b4f54bd9-6a0b-49c6-9a88-f0e6e9ba7ae2.png)

