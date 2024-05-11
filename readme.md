# 202031275_Muhammad Akbar Ramadhan_UTS
## _Pengolahan Citra_


![Proof](https://i.ibb.co/8jFys2Y/proof.jpg=150x150)


Project dibagi atas tiga tugas utama
- Mencetak gambar dengan gambar normal, channel merah, biru dan hijau
  - Untuk mencapai tahapan ini berikut adalah baris kode yang digunakan:
      ```sh
    img = img.imread("akbar.jpg")
    b = img[:,:,0]
    g = img[:,:,1]
    r = img[:,:,2]
    ```
    Diatas ini adalah tahapan pembentukan gambar, kemudian dengan matplotlib kita akan visualisasikan, untuk hasil dapat dilihat pada file .ipynb
    
    ![Proof](https://i.ibb.co/7R1kS88/image.png)

- Membuat histogram dari gambar-gambar yang sudah dipisahkan tadi
  - Untuk mencapai tujuan ini, berikut potongan kode yang digunakan:
    ```sh
    fig, axs = plt.subplots(2,2, figsize=(15,5))
    axs[0,0].hist(img_contrast.ravel(), 256, [0,256])
    axs[0, 0].set_title('Histogram Gambar Asli')
    
    
    axs[0,1].hist(r.ravel(), 256, [0,256])
    axs[0, 1].set_title('Histogram Red')
    
    
    axs[1,0].hist(g.ravel(), 256, [0,256])
    axs[1, 0].set_title('Histogram Green')
    
    
    axs[1,1].hist(b.ravel(), 256, [0,256])
    axs[1, 1].set_title('Histogram Blue')
    
    plt.show()
    ```
    Pada bagian ini, mahasiswa diminta agar dapat menampilkan besaran histogram pada masing-masing gambar, baik gambar utama maupun channel terpisah. Disini, menggunakan fungsi .hist agar dapat melakukan generate histogram.
    ![Proof](https://i.ibb.co/87gF8T4/image.png)
- Menentukan ambang batas bawah dan batas atas untuk mencetak hasil masking
  - Pada bagian ini, mahasiswa diminta untuk menentukan batas atas dan bawah agar bisa melakukan masking terhadap citra tulisan yang sudah dibuat warnanya. Berikut adalah potongan kode yang digunakan.
      ```sh
        img_akbar = cv2.imread('akbar.jpg')
        
        hsv = cv2.cvtColor(img_akbar, cv2.COLOR_BGR2HSV)
        
        l_biru = np.array([10,75,75])
        u_biru = np.array([145,255,255])
        
        l_hijau = np.array([5,50,50])
        u_hijau = np.array([90,255,255])
        
        l_merah = np.array([0,50,50])
        u_merah = np.array([15,255,255])
        
        l_merah_s = np.array([165,50,100])
        u_merah_s = np.array([250,255,255])
        
        biru_masking = cv2.inRange(hsv,l_biru,u_biru)
        hijau_masking = cv2.inRange(hsv,l_hijau,u_hijau)
        
        merah_masking = cv2.inRange(hsv,l_merah,u_merah)
        merah_masking2 = cv2.inRange(hsv,l_merah_s,u_merah_s)
        merah_masking = cv2.bitwise_or(merah_masking, merah_masking2)
      ```
      Pada bagian ini foto dimuat ulang, kemudian dengan menggunakan data dari histogram yang dimiliki mahasiswa akan mengisi parameter array nilai bawah dan nilai atas sesuai dengan kondisi histogram yang ada. Sehingga dengan nilai yang tepat, hasil masking akan muncul sesuai dengan channel warna masing-masing.
    ![Proof](https://i.ibb.co/Bg20kqV/download.png)
      
## Dasar Teori
Warna merupakan rentang spektrum yang terdapat dalam cahaya, baik itu cahaya murni maupun cahaya putih. Setiap warna memiliki identitas yang ditentukan oleh panjang gelombang dari cahaya tersebut. Penggunaan warna memiliki peranan yang penting dalam desain grafis, di mana warna tidak hanya menjadi elemen visual tetapi juga dapat memberikan daya tarik estetika yang kuat _Juandri, & Nizirwan Anwar. (2023)_. Teori warna dalam fisika menjelaskan bahwa warna adalah hasil dari cahaya yang dipantulkan oleh benda dan kemudian diterima oleh mata manusia. Warna juga dapat dijelaskan dengan model warna RGB (Red, Green, Blue), di mana warna yang terlihat dibentuk dari campuran intensitas dari tiga warna primer tersebut. Dalam desain grafis, penggunaan model warna RGB sangat umum karena dapat menghasilkan berbagai warna dengan mengatur proporsi dari tiga warna primer tersebut. Dengan demikian, warna bukan hanya fenomena fisik semata tetapi juga memiliki implikasi yang besar dalam pengalaman visual dan kreativitas desain.

## Daftar Pustaka
[Juandri, & Nizirwan Anwar. (2023). Pengenalan Warna Terhadap Objek Dengan Model Analisis Elemen Data Warna Gambar Berbasis Deep Neural Network. Jurnal Teknik Informatika, Ilmu Komputer, Universitas Esa Unggul](https://journal.mediapublikasi.id/index.php/bullet/article/download/2050/836)
