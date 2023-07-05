
# PROJECT UAS PENGOLAHAN CITRA A

Perkenalkan saya Cut Syahliza Nurrizky (201931010). Pada project ini saya mendapatkan judul tugas yaitu Deteksi plat nomor. 

Sebelum ke program, terlebih dahulu saya akan menjelaskan apa itu deteksi plat nomor. 

## Deteksi Plat Nomor
Deteksi plat nomor adalah proses identifikasi dan pengenalan karakter pada plat nomor kendaraan menggunakan teknik pengolahan citra dan pengenalan pola. Jupyter Notebook adalah sebuah lingkungan pengembangan yang populer untuk pemrograman interaktif dalam bahasa pemrograman Python. Jupyter Notebook memungkinkan Anda untuk menjalankan kode secara bertahap, mengamati hasilnya, dan membuat dokumentasi yang menjelaskan langkah-langkah yang diambil.

## Penjelasan Program

Langkah-langkah yang dilakukan dalam program tersebut adalah sebagai berikut:

Mengimpor pustaka yang diperlukan:
import cv2 as cv
import numpy as np
import matplotlib.pyplot as plt

Membaca citra plat nomor:
plat = cv.imread("platmotor.jpeg")

Mengubah citra ke skala abu-abu:
plat1 = cv.cvtColor(plat,cv.COLOR_BGR2GRAY)

Membuat pemotongan citra untuk mendapatkan wilayah plat nomor yang diinginkan:
img_crop = plat1[110:320,130:610]

Menampilkan citra asli dan plat terdeteksi dalam Jupyter Notebook:
fig, axes = plt.subplots(1, 2, figsize = (10, 11))
ax = axes.ravel()

ax[0].imshow(plat)
ax[0].set_title('Gambar Asli')
ax[1].imshow(img_crop, cmap = 'gray')
ax[1].set_title('Plat Terdeteksi')

Melakukan thresholding untuk menghasilkan citra biner menggunakan metode Otsu:
(these, imgb) = cv.threshold(img_crop, 0,255, cv.THRESH_BINARY + cv.THRESH_OTSU)

Menggunakan metode Canny untuk mendeteksi tepi pada citra plat terdeteksi:
edge = cv.Canny(img_crop, 100, 150)

Menampilkan citra biner dan citra tepi dalam Jupyter Notebook:
fig, axes = plt.subplots(1, 2, figsize = (10, 11))
ax = axes.ravel()

ax[0].imshow(cv.cvtColor(imgb, cv.COLOR_BGR2RGB))
ax[0].set_title('Binary Image')
ax[1].imshow(edge, cmap = 'gray')
ax[1].set_title('Edges Image')

Menyimpan citra asli dalam format PNG:
cv.imwrite("Gambar_Asli.png",plat)

Program tersebut membaca citra plat nomor "platmotor.jpeg" dan kemudian melakukan pra-pemrosesan dengan mengubahnya menjadi citra skala abu-abu dan memotong wilayah plat nomor yang diinginkan. Citra plat terdeteksi ditampilkan menggunakan matplotlib.

Selanjutnya, program melakukan thresholding menggunakan metode Otsu untuk menghasilkan citra biner, serta menggunakan metode Canny untuk mendeteksi tepi pada citra plat terdeteksi. Citra biner dan citra tepi ditampilkan kembali menggunakan matplotlib.

Terakhir, citra asli disimpan dalam format PNG dengan nama "Gambar_Asli.png".

## Sumber Materi
https://ichi.pro/id/deteksi-dan-kenali-plat-kendaraan-dengan-machine-learning-dan-python-bagian-1-deteksi-plat-nomor-dengan-wpod-net-133452590999842







