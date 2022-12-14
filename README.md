# CTRL+W ile kapanabilen 7zip kaynak kodu, derleyin ve kullanın.
Senelerdir kullandığım 7Zip'in eksik olduğu için sinir olduğum CTRL+W ile kapanabilme(yadırgıyor olabilirsiniz ama bu kadar yoğun kullanımdan sonra gerçekten ben bunaltan bir eksiklik bu. Bir de arşive not ekleyebilme özelliği ve arşiv açıldığında o notu arşiv görüntüleyicinin yanında görebilme olsa mükemmel olacak) özelliği ile alakalı yazılan bir yamanın gerçekten çalıştığını görebilmek ve hemen sistemime ayarlamak için bir cumartesi öğlesini ayırdığım çalışmadır.

CTRL+W ile kapanmayı reddeden 7zip'in fixlenmesi için 3 eylül 2022'de yazılmış v3 diff'in uygulanmış kaynak kod hali.

[screen-recorder-sat-sep-17-2022-14-07-13.webm](https://user-images.githubusercontent.com/5601326/190858365-54d74d6c-4631-4b04-be36-bbe5a4a072f8.webm)


## 64 Bit 7zip Yüklemesi İçin CTRL+W çalışan halinin ayarlanması

1. 64 Bit 7zip indirin ve yükleyin. https://sourceforge.net/projects/sevenzip/files/7-Zip/22.01/ (7z2201-x64.exe'i indirin) 
2. Bu repo'daki kodu indirip derleyin.
3. Derlenen 7zFM.exe ile orjinali değiştirin.


Not: Bu repo'nun yüklendiği tarihteki 7Zip versiyonu ve repo'daki 7zip kodunun ait olduğu versiyon 22.01'dir.

### Windows 10'da Derleme: 
Visual studio derleme araçlarının yüklenmiş olması gerekmektedir. https://visualstudio.microsoft.com/tr/downloads/#build-tools-for-visual-studio-2022 adresinden indirebilirsiniz(*C++ ile masaüstü geliştirme*yi seçerek yükleyin).

Başlat Menüsünde "x64 Native Tools Command Prompt for VS 2022" arayın ve bulun. (Başlat -> Çalıştır -> %comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\VC\Auxiliary\Build\vcvars64.bat" şeklinde de girebilirsiniz.)
Açılan Komut istemi penceresinde aşağıdaki kodları girin: 

``` 

cd <7zip-src klasörü yolu>\CPP\7zip

nmake NEW_COMPILER=1 MY_STATIC_LINK=1 CPU=AMD64 PLATFORM=x64

```
İşlem başarılı tamamlanmışsa aşağıdaki şekilde olacaktır.
![resim](https://user-images.githubusercontent.com/5601326/190855972-b7ea4998-bf65-49f1-935c-c19204db4f09.png)

Son olarak yüklemiş olduğunuz 7zFM.exe dosyası ile, aşağıda derlenmiş dizini verilen dosyayı değiştirin. 

```
Derlenen 7zFM.exe.
<7zip-src klasörü yolu> \CPP\7zip\Bundles\Fm\x64\
Yüklenen 7zFM.exe
C:\Program Files\7-Zip
```


# Bu aşamaya kadar gelirken okunan bağlantılardan bazıları.
- https://sourceforge.net/p/sevenzip/patches/402/
- https://sourceforge.net/p/sevenzip/feature-requests/1388/
- https://sourceforge.net/p/sevenzip/feature-requests/1561/
- https://sourceforge.net/p/sevenzip/discussion/45797/thread/5ffc7943/
- https://www.ski-epic.com/2012_compiling_7zip_on_windows_with_visual_studio_10/index.html
- https://stackoverflow.com/questions/55691927/how-to-compile-7zip-source-code-in-visual-studio-2017
- https://learn.microsoft.com/en-us/cpp/build/reference/nmake-reference?view=msvc-170
- https://stackoverflow.com/questions/22179737/cannot-compile-7zip-under-msvc2012
- https://github.com/myfreeer/7z-build-nsis/blob/master/7-zip-build.bat
- https://stackoverflow.com/questions/32109761/openssl-ml64-is-not-recognized-as-an-internal-or-external-command
- https://stackoverflow.com/questions/50703167/nmake-clean-command-line-property-on-clean-build-rebuild
