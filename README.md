# Tugas Akhir Praktikum Pemodelan Oseanografi
Repositori ini dibuat untuk memenuhi Tugas Akhir Praktikum Pemodelan Oseanografi. Repositori berisi script pemrograman yang digunakan dalam praktikum yaitu Adveksi-Difusi 1 Dimensi, Adveksi-Difusi 2 Dimensi, Hidrodinamika 1 Dimensi, dan  Model Data Gelombang National Buoy Data Center (NDBC). Bahasa pemrograman yang digunakan adalah python yang dapat diaplikasikan pada beberapa platform seperti Google Colaboratory dan Jupyter Notebook. Sedangkan untuk library yang digunakan kali ini adalah Numpy, Matplotlib, dan Siphon.
# Kelompok 15 :
1. Anggi Indira Rayhanifa_26050120120012_Oseanografi A
2. Christopher Agung Hutahaean_26050120130088_Oseanografi A
3. Indra Romadhon Oseanografi B
4. Ismail Basayep Oseanografi B
5. Muhamad Fadilah Nur Hafid Oseanografi B
6. Nadhifa Az Zahra Oseanografi B
7. Tanya Tristanova 26050120130042 Oseanografi A
# MODUL 1 : Adveksi-Difusi 1 Dimensi
Difusi  - adveksi merupakan proses transportasi materi dari suatu bagian sistem ke bagian yang lain sebagai hasil dari gerakan molekul acak yang melibatkan proses transportasi fluida dalam bentuk aliran rata – rata atau arus yang dipengaruhi oleh gaya gravitasi atau tekanan dan merupakan gerak horizontal. Secara matematis, persamaan difusi-adveksi dapat ditulis sebagai   , u Vu Du t x xx dengan u adalah konsentrasi zat dalam fluida, V adalah kecepatan adveksi, dan D adalah koefisien difusi. Model difusi-adveksi dapat ditemukan dalam kehidupan sehari-hari seperti pencemaran sungai maupun kebakaran hutan. Adveksi - Difusi merupakan suatu persamaan diferensial parsial.
# MODUL 2 : Adveksi-Difusi 2 Dimensi
Script
#!/usr/bin/env python
# coding: utf-8

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
# MODUL 3 : Hidrodinamika 1 Dimensi
bla bla bla
# MODUL 4 : Model Data Gelombang National Buoy Data Center (NDBC)
bla bla bla
