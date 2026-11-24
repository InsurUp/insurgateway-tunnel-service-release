<p align="center"><picture><source media="(prefers-color-scheme: dark)" srcset=".github/assets/insurup-logo-dark.svg"><img src=".github/assets/insurup-logo.svg" alt="InsurUp" width="360"></picture></p>

# InsurGateway Tunnel service `Stable`

Bu repoda kaynak kod yoktur, yalnızca InsurUp'ın yayın hattının yayımladığı imzalı InsurGateway Tunnel servisi yayın dosyaları bulunur.

## Kurulum

### Windows

Windows Server 2019 ya da Windows 10 1809 ve üstü gerekir; yönetici olarak açılmış bir PowerShell'de çalıştırın.

```powershell
Invoke-WebRequest https://github.com/InsurUp/insurgateway-tunnel-service-release/releases/latest/download/install.ps1 -OutFile install.ps1
powershell -ExecutionPolicy Bypass -File .\install.ps1
```

> [!NOTE]
> `install.ps1` yalnızca servisi kurar, tepsi ve pencere gelmez. Tepsi için https://github.com/InsurUp/insurgateway-tunnel-desktop-release reposundaki makine geneli `igw-tunnel-win-x64-Setup.exe` dosyasını kullanın.

Kaldırmak için:

```powershell
powershell -ExecutionPolicy Bypass -File .\install.ps1 -Uninstall
```

### Linux

systemd 239 ya da üstü gerekir. İkinci komut, InsurUp'a girilecek eşleştirme kodunu gösterir.

```sh
curl -fsSL https://github.com/InsurUp/insurgateway-tunnel-service-release/releases/latest/download/install.sh | sudo bash
sudo /opt/insurgateway-tunnel/current/igw-tunnel status
```

Kaldırmak için (önce betiği indirin):

```sh
curl -fsSL https://github.com/InsurUp/insurgateway-tunnel-service-release/releases/latest/download/install.sh -o install.sh
sudo bash ./install.sh --uninstall
```

### macOS

Kurulum betiği yoktur. Bu repoda yalnızca `igw-tunnel-osx-arm64.tar.gz` ve `igw-tunnel-osx-x64.tar.gz` arşivleri bulunur.

Kurulu servisler kendilerini buradaki son sürümden günceller (Windows ve Linux).

## Bütünlük

Her paketin (`.zip`, `.tar.gz`) bir `.sig` dosyası (güncelleyicinin paketi uygulamadan önce doğruladığı ECDSA P-256 imzası) ve bir `.sha256` dosyası vardır.

<details>
<summary>SHA-256'yı elle denetle</summary>

Dosyalar aynı klasörde. Özet değerleri aynı olmalıdır.

### Windows

```powershell
(Get-FileHash .\igw-tunnel-win-x64.zip -Algorithm SHA256).Hash
Get-Content .\igw-tunnel-win-x64.zip.sha256
```

### Linux

```sh
sha256sum -c igw-tunnel-linux-x64.tar.gz.sha256
```

### macOS

```sh
shasum -a 256 -c igw-tunnel-osx-arm64.tar.gz.sha256
```

</details>

## İletişim

https://www.insurup.com
