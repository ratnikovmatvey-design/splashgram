# Splashgram

![Splashgram Logo](.github/Splashgram.png) ![SplashgramMascot](.github/SplashgramMascot.png)

[ English  |   [Русский](README-RU.md) ]

## Features

- Full ghost mode (flexible)
- Messages history
- Anti-recall
- Font customization
- Streamer mode
- Local Telegram Premium
- Translator
- Media preview & quick reaction on force click (macOS)
- Enhanced appearance

And many more. Check out our [Documentation](https://docs.splashgram.one/desktop/).

<h3>
  <details>
    <summary>Preview</summary>
    <table>
      <tr>
        <td><img src='.github/demos/demo1.png' width='268' alt='Preferences'></td>
        <td><img src='.github/demos/demo2.png' width='268' alt='Splashgram Options'></td>
        <td><img src='.github/demos/demo3.png' width='268' alt='Message Filters'></td>
      </tr>
      <tr>
        <td><img src='.github/demos/demo4.png' width='268' alt='Appearance'></td>
        <td><img src='.github/demos/demo5.png' width='268' alt='Chats'></td>
      </tr>
    </table>
  </details>
</h3>

## Downloads

### Windows

#### Official

You can download prebuilt Windows binary from [Releases tab](https://github.com/Splashgram/SplashgramDesktop/releases) or from
the [Telegram channel](https://t.me/SplashgramReleases).

#### Winget

```bash
winget install RadolynLabs.SplashgramDesktop
```

#### Scoop

```bash
scoop bucket add extras
scoop install splashgram
```

#### Self-built

Follow [official guide](https://github.com/Splashgram/SplashgramDesktop/blob/dev/docs/building-win-x64.md) if you want to
build by yourself.

### macOS

#### Official

You can download prebuilt macOS package from [Releases tab](https://github.com/Splashgram/SplashgramDesktop/releases).

#### Homebrew

```bash
brew install --cask splashgram
```

### Arch Linux

#### From source (recommended)

Install `splashgram-desktop` from [AUR](https://aur.archlinux.org/packages/splashgram-desktop).

#### Prebuilt binaries

Install `splashgram-desktop-bin` from [AUR](https://aur.archlinux.org/packages/splashgram-desktop-bin).

Note: these binaries aren't officially maintained by us.

### NixOS

#### Flake (recommended)

Install `splashgram-desktop` from [ndfined-crp/splashgram-desktop](https://github.com/ndfined-crp/splashgram-desktop)

#### Nixpkgs

Install `splashgram-desktop` from [nixpkgs](https://search.nixos.org/packages?channel=unstable&show=splashgram-desktop)

### ALT Linux

[Sisyphus](https://packages.altlinux.org/en/sisyphus/srpms/splashgram-desktop/)

### Gentoo Linux

See [this repository](https://codeberg.org/OverLessArtem/splashgram-ebuild-gentoo) for installation manual.

### Void Linux
See [this repository](https://codeberg.org/OverLessArtem/splashgram-template-void) for installation manual.

### EPM

`epm play splashgram`

### Fedora

From [RPM Fusion](https://admin.rpmfusion.org/pkgdb/package/free/splashgram-desktop/) repository.

```bash
dnf install splashgram-desktop
```

### Any other Linux distro

Flatpak: https://github.com/0FL01/SplashgramDesktop-flatpak

Or follow the [official guide](https://github.com/Splashgram/SplashgramDesktop/blob/dev/docs/building-linux.md).

## Donation

Enjoy using **Splashgram**? Consider sending us a tip!

[Here's available methods.](https://docs.splashgram.one/donate/)

## Credits

### Telegram clients

- [Telegram Desktop](https://github.com/telegramdesktop/tdesktop)
- [Kotatogram](https://github.com/kotatogram/kotatogram-desktop)
- [64Gram](https://github.com/TDesktop-x64/tdesktop)
- [Forkgram](https://github.com/forkgram/tdesktop)

### Libraries used

- [JSON for Modern C++](https://github.com/nlohmann/json)
- [SQLite](https://github.com/sqlite/sqlite)
- [sqlite_orm](https://github.com/fnc12/sqlite_orm)
- [androidx sources](https://github.com/androidx/androidx)

### Icons

- [Solar Icon Set](https://www.figma.com/community/file/1166831539721848736)

### Bots

- [TelegramDB](https://t.me/tgdatabase) for username lookup by ID (until closing free inline mode at 2 April 2026)
