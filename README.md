# qBittorrent-flatpak
*Unofficial* repository of [qBittorrent](https://github.com/qbittorrent/qBittorrent) (flatpak) package

## For package maintainer
Refer to [maintainer.md](./maintainer.md) file

## Just want to use qBittorrent
* First, install flatpak: [Getting Flatpak](https://flatpak.org/getting)
* If your distro supports "click to download" then use the following link:<br>
  [Latest stable](https://cdn.rawgit.com/Chocobo1/qBittorrent-flatpak/master/qBittorrent.flatpakref)
* Otherwise do the following:
  * Install
    ```shell
    flatpak install --from https://raw.githubusercontent.com/Chocobo1/qBittorrent-flatpak/master/qBittorrent.flatpakref --assumeyes
    ```
  * Run
    ```shell
    flatpak run org.qBittorrent.qbittorrent
    ```
  * Update:
    ```shell
    flatpak update --app org.qBittorrent.qbittorrent
    ```
  * Remove:
    ```shell
    flatpak uninstall org.qBittorrent.qbittorrent
    ```
