## 1. Prepare build environment
  * Install flatpak<br>
    See: [Getting Flatpak](http://flatpak.org/getting.html)
  * Install required SDK & runtime:
    ```shell
    flatpak remote-add kde --from https://distribute.kde.org/kderuntime.flatpakrepo
    flatpak install kde org.kde.Platform org.kde.Sdk
    ```

## 2. Build qBittorrent
  * Clone this repository:
    ```shell
    git clone https://github.com/Chocobo1/qBittorrent-flatpak.git
    ```
  * Start building qBittorrent
    * Stable release:
      ```shell
      flatpak-builder ".build" "qBittorrent.stable.json" --repo=flatpak_qbt_repo --ccache --jobs=$(nproc --ignore=1) --verbose
      ```
    * Development branch:
      ```shell
      flatpak-builder ".build" "qBittorrent.dev.json" --repo=flatpak_qbt_repo --ccache --jobs=$(nproc --ignore=1) --verbose
      ```
    This will create a flatpak repository: `flatpak_qbt_repo`

## 3. Installation
  * Local
    * Add the created repository and name it `qbt`:
      ```shell
      flatpak remote-add qbt flatpak_qbt_repo  # --no-gpg-verify
      ```
    * Install:
      ```shell
      flatpak install qbt org.qBittorrent.qbittorrent
      ```
  * Run qBittorrent:
    ```shell
    flatpak run org.qBittorrent.qbittorrent
    ```

## 4. Maintainence
  * Sign the repo with GPG:
    ```shell
    flatpak build-sign flatpak_qbt_repo org.qBittorrent.qbittorrent <Branch> --gpg-sign=<KEY>
    ```
  * Generate deltas (use more space on server for faster client download):
    ```shell
    flatpak build-update-repo --generate-static-deltas --prune flatpak_qbt_repo --gpg-sign=<KEY>
    ```
  * Remove qBittorrent repo:
    ```shell
    flatpak remote-delete qbt
    ```
  * Remove SDK & runtime:
    ```shell
    flatpak uninstall org.kde.Platform.Locale org.kde.Platform org.kde.Sdk.Locale org.kde.Sdk
    flatpak remote-delete kde
    ```
