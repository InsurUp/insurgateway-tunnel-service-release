[🇹🇷 TR](./README.tr.md)

<p align="center"><picture><source media="(prefers-color-scheme: dark)" srcset=".github/assets/insurup-logo-dark.svg"><img src=".github/assets/insurup-logo.svg" alt="InsurUp" width="360"></picture></p>

# InsurGateway Tunnel service `Stable`

This repository holds no source code, only the signed InsurGateway Tunnel service release files that InsurUp's release pipeline publishes.

## Install

### Windows

Needs Windows Server 2019 or Windows 10 1809 or later, in a PowerShell opened as administrator.

```powershell
Invoke-WebRequest https://github.com/InsurUp/insurgateway-tunnel-service-release/releases/latest/download/install.ps1 -OutFile install.ps1
powershell -ExecutionPolicy Bypass -File .\install.ps1
```

> [!NOTE]
> `install.ps1` installs the service alone, with no tray or window. For the tray, use the machine-wide `igw-tunnel-win-x64-Setup.exe` from https://github.com/InsurUp/insurgateway-tunnel-desktop-release.

Remove:

```powershell
powershell -ExecutionPolicy Bypass -File .\install.ps1 -Uninstall
```

### Linux

Needs systemd 239 or newer. The second command shows the pairing code to enter in InsurUp.

```sh
curl -fsSL https://github.com/InsurUp/insurgateway-tunnel-service-release/releases/latest/download/install.sh | sudo bash
sudo /opt/insurgateway-tunnel/current/igw-tunnel status
```

Remove (download the script first):

```sh
curl -fsSL https://github.com/InsurUp/insurgateway-tunnel-service-release/releases/latest/download/install.sh -o install.sh
sudo bash ./install.sh --uninstall
```

### macOS

No install script. This repository holds only the archives `igw-tunnel-osx-arm64.tar.gz` and `igw-tunnel-osx-x64.tar.gz`.

Installed services update themselves from the latest release here (Windows and Linux).

## Integrity

Each package (`.zip`, `.tar.gz`) has a `.sig`, an ECDSA P-256 signature that the updater verifies before it applies the package, and a `.sha256`.

<details>
<summary>Check the SHA-256 by hand</summary>

Files in the same folder. The hash values must match.

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

## Contact

https://www.insurup.com
