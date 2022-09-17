# 7zip source code that can be closed with CTRL+W, compile and use.
Closing with CTRL+W, which I've been using for years because of the missing 7Zip (you may be surprised, but this is a shortcoming that really overwhelms me after such heavy use. It would be great if there was also the ability to add notes to the archive and to be able to see that note next to the archive viewer when the archive is opened) This is the work that I took a Saturday afternoon to see that a patch written about the feature is actually working and to set it up on my system immediately.

Applied source code version of v3 diff written on September 3, 2022 to fix 7zip refusing to close with CTRL+W.


## Setting CTRL+W running state for 64 Bit 7zip Installation

1. Download and install 64 Bit 7zip. https://sourceforge.net/projects/sevenzip/files/7-Zip/22.01/ (Download 7z2201-x64.exe)
2. Download and compile the code from this repo.
3. Replace the original with the compiled 7zFM.exe.


Note: The 7zip version at the time this repo was installed and the version to which the 7zip code in the repo belongs is 22.01.

### Compiling on Windows 10:
Visual studio build tools must be installed. You can download it from https://visualstudio.microsoft.com/en/downloads/#build-tools-for-visual-studio-2022 (*Selectively install desktop development with C++).

Search and locate "x64 Native Tools Command Prompt for VS 2022" in the Start Menu. (You can also enter Start -> Run -> %comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\VC\Auxiliary\Build\vcvars64.bat".)
In the Command Prompt window that opens, enter the following codes:

```

cd <path to 7zip-src folder>\CPP\7zip

nmake NEW_COMPILER=1 MY_STATIC_LINK=1 CPU=AMD64 PLATFORM=x64

```
If the process is completed successfully, it will be as follows.
![image](https://user-images.githubusercontent.com/5601326/190855972-b7ea4998-bf65-49f1-935c-c19204db4f09.png)

Finally, replace the 7zFM.exe file you downloaded with the file with the compiled directory below.

```
Compiled 7zFM.exe.
<path to 7zip-src folder> \CPP\7zip\Bundles\Fm\x64\
Installed 7zFM.exe
C:\Program Files\7-Zip
```


# Some of the links read on the way to this stage.
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
