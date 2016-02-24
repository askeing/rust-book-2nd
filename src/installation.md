# 安裝

使用 Rust 的第一步就是安裝。
一般來說，在這一章你需要網路去執行指令，因為我們需要從網路上下載 Rust。

我們將會提供給一些終端機的指令，這些指令都會用 `$` 開頭。
你不需要輸入這些 `$`，他們只是用來標示每一行指令。
網路上許多教學和範例都會依照以下的慣例撰寫：以一般使用者身份執行的指令使用 `$` 開頭，以管理者身份執行的指令使用 `#` 開頭。

## 安裝在 Linux 或 Mac

如果在 Linux 或 Mac 上，我們只需要開啟終端機並輸入：

```bash
$ curl -sSf https://static.rust-lang.org/rustup.sh | sh
```

這樣就會下載安裝腳本，然後開始安裝。
當全部完成，你將會看到：

```text
Welcome to Rust.

This script will download the Rust compiler and its package manager, Cargo, and
install them to /usr/local. You may install elsewhere by running this script
with the --prefix=<path> option.

The installer will run under ‘sudo’ and may ask you for your password. If you do
not want the script to run ‘sudo’ then pass it the --disable-sudo flag.

You may uninstall later by running /usr/local/lib/rustlib/uninstall.sh,
or by running this script again with the --uninstall flag.

Continue? (y/N)
```

接著按下 `y` 表示同意，然後按照提示安裝。

## 安裝在 Windows

如果你使用 Windows，請下載合適版本的[安裝檔][install-page]

[install-page]: https://www.rust-lang.org/install.html

## 移除

移除 Rust 跟安裝一樣簡單。
在 Linux 或 Mac 上，只要執行移除指令就好：

```bash
$ sudo /usr/local/lib/rustlib/uninstall.sh
```

如果是安裝 Windows 安裝檔，重新執行 `.msi` 檔，然後他會出現移除的選項。

## 故障排除

當我們安裝好 Rust 後，我們可以開啟終端機，然後輸入：

```bash
$ rustc --version
```

你將會看到版本號、commit hash 及 commit 的日期。

如果你成功了，代表 Rust 安裝成功了！恭喜！

如果沒有成功，而你使用 Windows，請確認 Rust 有設定在你的 %PATH% 系統環境變數內。
如果沒有，重新執行安裝檔，在 "Change, repair, or remove installation" 頁面選擇 "Change"，接著確定 "Add to PATH" 有被勾選。

如果仍然沒有成功，有許多地方可以獲得協助。
最簡單的是連上 [irc.mozilla.org 的 #rust IRC 頻道][irc]，可以使用 [Mibbit][mibbit] 連上 IRC。
按下連結，然後就可以跟能幫助我們的 Rustaceans（我們用以自稱的暱稱）聊天。
其他的資源還包括了[使用者論壇][users]和 [Stack Overflow][stackoverflow]。

[irc]: irc://irc.mozilla.org/#rust
[mibbit]: http://chat.mibbit.com/?server=irc.mozilla.org&channel=%23rust
[users]: https://users.rust-lang.org/
[stackoverflow]: http://stackoverflow.com/questions/tagged/rust

## 本機文件

安裝檔同時也安裝一份文件副本在本機，所以我們可以直接離線閱讀這份文件。
在 UNIX 系統的位置是 `/usr/local/share/doc/rust`。
在 Windows，文件放在 Rust 的安裝目錄下的 `share/doc` 目錄。
