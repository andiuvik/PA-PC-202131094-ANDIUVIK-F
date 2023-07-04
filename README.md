
# Deteksi Buah_Andi Uvik_202131094_UAS Pengolahan Citra

Deteksi objek berdasarkan warna dalam pengolahan citra adalah teknik yang digunakan untuk mengidentifikasi dan memisahkan objek dalam citra berdasarkan perbedaan warna mereka. Metode ini berguna ketika objek yang ingin dideteksi memiliki karakteristik warna yang konsisten dan berbeda secara signifikan dengan latar belakangnya.

Proses deteksi objek berdasarkan warna melibatkan beberapa langkah, antara lain:
-Konversi Warna: Citra awalnya mungkin berada dalam format warna yang berbeda, seperti RGB, BGR, HSV, atau lainnya. Pertama, citra dikonversi ke format warna yang paling sesuai untuk analisis berdasarkan warna, seperti HSV.

-Definisikan Rentang Warna: Rentang warna yang mewakili objek yang ingin dideteksi ditentukan. Rentang ini dapat didefinisikan dengan menggunakan nilai ambang (threshold) pada komponen warna tertentu, seperti hue (tingkat warna), saturation (kejenuhan), dan value (nilai intensitas).

// Penjelasan Syntax dari deteksi buah

import cv2
import numpy as np
import matplotlib.pyplot as plt
penjelasan: 
-import adalah fungsi Python untuk memanggil modul di luar fungsi dasar yang disediakan.
-cv2 adalah nama modul Python yang digunakan untuk memanggil fungsi-fungsi OpenCV.
-numpy modul Python untuk pengolahan matriks (ingat bahwa citra pada OpenCV dianggap sebagai matrix) matplotlib modul Python untuk melakukan fungsi plotting

image = cv2.imread('buahh.jpg')
penjelasan: cv2.imread perintah yang digunakan pada modul cv2 untuk memanggil citra dan menunjukkan bahwa citra ‘buahh.jpg’ disimpan pada variable bernama image.

image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
Penjelasan: cv2.COLOR_RGB2GRAY merupakan perintah untuk menkonversi citra berwarna menjadi gray (abu-abu) dimana fungsi tersebut ada pada library cv2

lower_red = np.array([0, 0, 0])
upper_red = np.array([100, 50, 255])
lower_yellow = np.array([0, 130, 130])
upper_yellow = np.array([30, 255, 255])
lower_green = np.array([20, 100, 0])
upper_green = np.array([45, 255, 255])
Penjelasan: untuk deteksi buah dengan mengatur nilai-nilai lower dan upper. Setiap rentang warna ditentukan dalam format [B, G, R] menggunakan array NumPy. Misalnya, rentang warna merah didefinisikan sebagai lower_red = [0, 0, 100] dan upper_red = [100, 100, 255].

mask_red = cv2.inRange(image, lower_red, upper_red)
mask_yellow = cv2.inRange(image, lower_yellow, upper_yellow)
mask_green = cv2.inRange(image, lower_green, upper_green)
Penjelasan:  fungsi cv2.inRange() untuk menciptakan citra biner yang hanya berisi piksel-piksel yang berada dalam rentang warna yang ditentukan untuk setiap deteksi buah. Misalnya, mask_red = cv2.inRange(image, lower_red, upper_red) akan menghasilkan citra biner yang hanya berisi piksel-piksel dengan warna merah dalam rentang yang ditentukan.

result_red = cv2.bitwise_and(image_rgb, image_rgb, mask=mask_red)
result_yellow = cv2.bitwise_and(image_rgb, image_rgb, mask=mask_yellow)
result_green = cv2.bitwise_and(image_rgb, image_rgb, mask=mask_green)
penjelasan: Menggunakan operasi bitwise AND (cv2.bitwise_and()) untuk menerapkan hasil deteksi pada citra asli. Hasil ini akan menyoroti piksel-piksel yang sesuai dengan rentang warna yang ditentukan.

plt.figure(figsize=(12, 4))
plt.subplot(141)
plt.imshow(image_rgb)
plt.title('Asli')
plt.subplot(142)
plt.imshow(result_red)
plt.title('Merah')
plt.subplot(143)
plt.imshow(result_yellow)
plt.title('Kuning')
plt.subplot(144)
plt.imshow(result_green)
plt.title('Hijau')
plt.tight_layout()
plt.show()
Penjelasan:
-plt.subplot() untuk membuat grid subplot dengan empat kolom. Setiap subplot menampilkan hasil deteksi buah berdasarkan warna yang berbeda.
-plt.imshow() untuk menampilkan hasil deteksi
-image_rgb sebagai citra latar belakang dan menggunakan masker deteksi buah sebagai masker.
-plt.title() memberikan judul pada setiap subplot.
## Penjelasan Syntax
