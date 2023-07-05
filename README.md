
# Deteksi Buah

#### Alfisyam (202031261)

Ini project untuk melakukan deteksi buah menggunakan OpenCV dan Python dalam lingkungan Jupyter Notebook. OpenCV adalah pustaka pemrosesan gambar yang kuat yang digunakan secara luas dalam pengembangan aplikasi penglihatan komputer. Dalam tutorial ini, kita akan menggunakan OpenCV untuk mendeteksi objek buah dalam gambar.

## Persyaratan

Sebelum memulai, pastikan Anda memiliki lingkungan Python yang terinstal di komputer Anda. Selain itu, pastikan Anda telah menginstal pustaka OpenCV dan Jupyter Notebook. Anda dapat menginstalnya dengan menggunakan pip, dengan menjalankan perintah berikut di terminal atau command prompt:

```
pip install opencv-python
pip install jupyter
```

## Langkah 1: Impor Pustaka dan Baca Gambar

Pertama, kita perlu mengimpor pustaka yang diperlukan, yaitu `cv2` dari OpenCV dan `matplotlib` untuk menampilkan gambar. Selain itu, kita juga perlu mengatur konfigurasi Jupyter Notebook agar gambar yang ditampilkan akan ditampilkan di dalam notebook.

```python
import cv2
from matplotlib import pyplot as plt

# Konfigurasi untuk menampilkan gambar di Jupyter Notebook
%matplotlib inline
```

Selanjutnya, kita dapat membaca gambar yang akan kita deteksi. Misalkan kita memiliki gambar dengan nama file "buah.jpg". Untuk membaca gambar tersebut, kita dapat menggunakan fungsi `cv2.imread()`.

```python
image_path = "buah.jpg"
image = cv2.imread(image_path)
```

## Langkah 2: Ubah Gambar ke Skala Keabuan

Untuk mempermudah proses deteksi, kita akan mengubah gambar berwarna menjadi gambar skala keabuan. Ini dapat dilakukan dengan menggunakan fungsi `cv2.cvtColor()`.

```python
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
```

## Langkah 3: Deteksi Buah

Selanjutnya, kita akan menggunakan deteksi objek Haar Cascade untuk mendeteksi buah dalam gambar. Haar Cascade adalah algoritme deteksi objek yang umum digunakan dalam penglihatan komputer. OpenCV menyediakan beberapa file cascade yang sudah dilatih untuk deteksi objek tertentu, termasuk buah.

```python
cascade_path = "haarcascade_fruit.xml"
fruit_cascade = cv2.CascadeClassifier(cascade_path)

# Deteksi buah dalam gambar
fruits = fruit_cascade.detectMultiScale(gray_image, scaleFactor=1.1, minNeighbors=5, minSize=(30, 30))
```

Pada contoh di atas, kita menggunakan file cascade "haarcascade_fruit.xml" untuk mendeteksi buah. Anda dapat menggunakan cascade yang telah dilatih atau melatih cascade Anda sendiri dengan dataset pelatihan yang sesuai.

## Langkah 4: Tampilkan Hasil Deteksi

Terakhir, kita akan menampilkan gambar asli dengan kotak pembatas yang mengelilingi objek buah yang terdeteksi.

```python
# Gambar kotak pembatas pada buah yang terdeteksi
for (x, y, w, h) in fruits:
    cv2.rectangle(image, (x, y), (x+w, y+h), (

0, 255, 0), 2)

# Tampilkan gambar dengan kotak pembatas
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.axis("off")
plt.show()
```

Hasil deteksi akan ditampilkan dalam sebuah plot di Jupyter Notebook.

## Kesimpulan

Dalam tutorial ini, kita telah melihat cara menggunakan OpenCV dalam Python untuk mendeteksi objek buah dalam gambar. Dengan menggunakan deteksi objek Haar Cascade, kita dapat dengan mudah mendeteksi objek buah dalam gambar dan menampilkan hasilnya. Anda dapat menggunakan pendekatan ini sebagai dasar untuk aplikasi penglihatan komputer yang lebih kompleks yang melibatkan deteksi objek.