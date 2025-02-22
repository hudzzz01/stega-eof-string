### @kentung 🚩

### hudzaifahzzzzzz@gmail.com

#### +62895-3669-75992

Simple Way use add to POM.xml from jitpack.io 
#
[![](https://jitpack.io/v/hudzzz01/stega-eof-string.svg)](https://jitpack.io/#hudzzz01/stega-eof-string)
```
    <repositories>
        <repository>
            <id>jitpack.io</id>
            <url>https://jitpack.io</url>
        </repository>
    </repositories>

```

```
<dependencies>
        <dependency>
            <groupId>com.github.hudzzz01</groupId>
            <artifactId>stega-eof-string</artifactId>
            <version>-3f39500c83-1</version>
        </dependency>
</dependencies>

```

# SteganoService

## Deskripsi

`SteganoService` adalah layanan yang menyediakan fungsi steganografi dasar untuk menyisipkan dan mengekstrak pesan dari
gambar.

## Fitur

1. **Menyisipkan Pesan ke Gambar (`stegano`)**
    - Membaca gambar sebagai byte array.
    - Mengonversi pesan ke byte array.
    - Menggabungkan byte dari gambar dengan pesan.
    - Menyimpan kembali hasil modifikasi ke file output.

2. **Mengekstrak Pesan dari Gambar (`extrackMessage`)**
    - Membaca gambar sebagai byte array.
    - Mengambil pesan dari bagian akhir gambar berdasarkan panjang pesan yang diberikan.
    - Mengonversi byte menjadi string dan mengembalikannya.

## Struktur Kode

### `stegano(String message, File inputImage) -> Integer[]`

- **Parameter**:
    - `message`: Pesan yang akan disisipkan.
    - `inputImage`: File gambar yang akan digunakan.
- **Return**:
    - `[1, messageByte.length]` jika berhasil.
    - `[0, 0]` jika gagal.

### `extrackMessage(File imageForExtractMessage, int messageLength) -> String[]`

- **Parameter**:
    - `imageForExtractMessage`: File gambar yang berisi pesan tersembunyi.
    - `messageLength`: Panjang pesan yang akan diekstrak.
- **Return**:
    - `{"1", extractedMessage}` jika berhasil.
    - `{"0", ""}` jika gagal.

### Fungsi Pendukung

- `extractMessageData(int startIndex, int messageLength, byte[] imageData) -> byte[]`: Mengambil pesan tersembunyi dari
  byte array gambar.
- `toStringFromByte(byte[] data) -> String`: Mengonversi byte array menjadi string.
- `getImageByte(File file) -> byte[]`: Membaca gambar dan mengembalikannya dalam bentuk byte array.
- `getMessageByte(String message) -> byte[]`: Mengonversi string pesan menjadi byte array.
- `combineByte(byte[] imageByte, byte[] messageByte) -> byte[]`: Menggabungkan byte array gambar dan pesan.
- `writeByteToFile(byte[] data, File file) -> Boolean`: Menulis kembali data yang telah dimodifikasi ke file output.

## Cara Penggunaan

1. **Menyisipkan Pesan**:
   ```java
   SteganoService steganoService = new SteganoService();
   File inputImage = new File("InputImage/sample.jpeg");
   Integer[] result = steganoService.stegano("Pesan rahasia", inputImage);
   ```
   Jika `result[0] == 1`, maka penyisipan berhasil.

2. **Mengekstrak Pesan**:
   ```java
   String[] extractedMessage = steganoService.extrackMessage(new File("OutputImage/sample.jpeg"), 14);
   ```
   Jika `extractedMessage[0] == "1"`, maka pesan berhasil diekstrak.

## Kesimpulan

Layanan ini menyediakan metode sederhana untuk menyisipkan dan mengekstrak pesan dari gambar menggunakan teknik
steganografi berbasis byte array.

