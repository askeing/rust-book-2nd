# Hello, world!

現在 Rust 已經安裝好了，讓我們開始寫第一個 Rust 程式。
傳統上，學習一個新的語言時，我們都會撰寫一個小程式去印出 "Hello, world!" 在螢幕上。
本節我們會遵循這個傳統。

從簡單的小程式開始的好處，是你能快速的驗證你的編譯器已經安裝完成，而且運作良好。
把資訊印在螢幕上也是個很常見的事情，所以早點練習沒什麼不好。

> 註：本書假設你已經有基本的指令熟悉程度。
> Rust 不指定編輯器、工具、等等，所以如果你喜歡使用 IDE，這也是個選擇。

## 建立專案檔

首先，建立一個檔案來放你的程式碼。
Rust 不在乎你的程式碼放在哪，但我會建議你建立一個 *projects* 的目錄在 home 目錄底下，並且把所有你的專案都放在裡面。
開啟終端機並輸入以下指令來替專案建立目錄：

```bash
$ mkdir ~/projects
$ cd ~/projects
$ mkdir hello_world
$ cd hello_world
```

> 註：如果你使用 Windows 而且不是使用 PowerShell，則 `~` 應該沒有作用。
> 參考適合你的文件去設定你的 shell。

## 撰寫並執行 Rust 程式

接著，建立一個原始碼檔案 *main.rs*。
Rust 的檔案永遠以 *.rs* 作為結尾。
如果你的檔案名稱有超過一個單字，使用底線去區分它們；例如，你應該使用 *hello_world.rs* 命名，而不是 *helloworld.rs*。

現在開啟建立好的 *main.rs* 檔案，然後輸入以下程式碼：

```rust
fn main() {
    println!("Hello, world!");
}
```

存檔，然後回到你的終端機視窗。
在 Linux 或 OSX 下，輸入以下指令：

```bash
$ rustc main.rs
$ ./main
Hello, world!
```

在 Windows 下，只需要把 `main` 換成 `main.exe`。
不論你的作業系統為何，你應該能看到字串 `Hello, world!` 印在你的終端機上。
如果你成功了，那麼恭喜你！
你正式地寫出了 Rust 程式。這讓你成為了 Rust 程式設計師！歡迎你！

## 剖析 Rust 程式

現在，讓我們細細檢視你的 "Hello, world!" 程式倒底發生了什麼。
這是第一個謎團：

```rust
fn main() {

}
```

這幾行定義了 Rust 中的 *函式* (function)。
而 `main` 函式比較特殊：他是所有 Rust 城市的開始之處。
第一行意指：『我要宣告一個名叫 `main` 的函式，他沒有參數也不回傳任何東西。』
如果函式有參數，它會放在括號中間（`(` and `)`），而因為我們沒有回傳任何東西，所以我們可以忽略回傳的型態。

另外，注意函式的內容被大括號（`{` and `}`）給包起來。
Rust 要求大括號要在所有函式的內容外面。
考量到好的程式樣式，我們會把一個大括號放在函式宣告的同一行，中間隔一個空白。

在 `main()` 函式中：

```rust
    println!("Hello, world!");
```

這一行做了這個小程式的所有工作：印出文字到螢幕上。
這邊有許多很重要的細節。
第一個是縮排是四個空白，而不是 tabs。

第二個重要的部分是 `println!()` 這行。
這個在 Rust 叫做 *[巨集][macro]* (macro)，這是 Rust 達成 metaprogramming 的方式。
如果此處改用函式的話，會看起來像是 `println()`（沒有 ! 符號）。
我們將會在之後討論 Rust 巨集的更多細節，但是現在你只需要知道，當你看到 `!` 的時候，代表你正在呼叫一個巨集而不是一般的函式。

[macro]: macros.html

接著 `"Hello, world!"` 是一個 *字串* (string)。
我們傳遞這個字串作為參數給 `println!`，然後它將字串印在螢幕上。
夠簡單吧！

程式中每一行都以分號（`;`）結尾。
Rust 是個 *表達式導向* (expression oriented) 的語言，這代表著大多數的東西都是表達式，而不是陳述式 (statements)。
`;` 代表著這個表達式已經結束，而且下一個正準備開始。
Rust 程式碼的大多數行都是以 `;` 結尾。

## 編譯和執行是分開的步驟

在 "撰寫並執行 Rust 程式" 中，我們告訴你如何執行一個新建的程式。
現在讓我們分解流程，檢查每一步。

執行 Rust 程式之前，你需要編譯它。
你可以使用 Rust 編譯器，輸入 `rustc` 指令並傳遞原始碼的檔名給它，像這樣：

```bash
$ rustc main.rs
```

如果你有 C 或 C++ 的背景，你會注意到這跟 `gcc` 或 `clang` 很類似。
編譯成功之後，Rust 應該會輸出一個執行檔，你可以在 Linux 或 OSX 下輸入 `ls` 指令：

```bash
$ ls
main  main.rs
```

在 Windows 下，你可以輸入：

```bash
$ dir
main.exe  main.rs
```

這告訴我們有兩個檔案在這：以 `.rs` 作為副檔名的原始檔，以及執行檔（在 Windows 是 `main.exe`，其他則是 `main`）。
接著我們唯一要做的就只剩下執行 `main` 或 `main.exe` 了：

```bash
$ ./main  # or main.exe on Windows
```

如果 *main.rs* 就是你的 "Hello, world!" 程式，那他將會印出 `Hello, world!` 在你的終端機上。

如果你以前是學動態語言，像 Ruby、Python、或 JavaScript，你可能會不習慣編譯和執行程式是分開的步驟。
Rust 是個 *提前編譯* 的語言，這代表你可以編譯程式，然後把程式給其他人，他們可以在沒有安裝 Rust 的情況下執行程式。
如果你給一個人 `.rb` 或 `.py` 或 `.js` 檔，換句話說，他也必須要有安裝好的 Ruby、Python、或 JavaScript 應用（個別地），但只需要一個指令去編譯並執行你的程式。
在程式語言的設計中，所有事情都是取捨。

簡單的程式只需要用 `rustc` 直接編譯就好了，但是如果你的專案成長了，你會希望能夠管理專案的所有選項，並且能簡單的分享你的程式碼給其他人和專案。
下一節，我們將會介紹給你一個叫做 Cargo 的工具，他可以幫你撰寫真實世界的 Rust 程式。

# Hello, Cargo!

Cargo 是 Rust 的建置系統跟套件管理器，而且 Rustaceans 會使用 Cargo 去管理他們的 Rust 專案。
Cargo 管理三件事：建置你的程式碼、下載你的程式碼所依賴的函式庫 (libraries)、以及建置這些函式庫。
我們把這些你的程式所依賴的函式庫叫做 "依賴關係" (dependencies)，因為你的程式碼依賴他們。

最簡單的 Rust 城市不會有任何依賴關係，所以現在你只會用到第一部份的功能。
當你撰寫更複雜的 Rust 程式後，你將會希望加入依賴關係，而且如果你從 Cargo 開始的話，那會簡單很多。

許多主要的 Rust 專案都使用 Cargo，我們假設在本書後面的章節你都會使用它。
如果你使用官方的安裝檔，Cargo 將會隨著 Rust 一起裝好。
如果你用其他方法安裝 Rust，你可以輸入以下指令檢查是否已經裝好 Cargo：

```bash
$ cargo --version
```

在終端機內，如果你能看到版本號碼，那就太好了！
如果你看到錯誤訊息像 `command not found`，則你應該要查閱你安裝 Rust 時的文件，確定 Cargo 是否需要另外安裝。

## 轉換到 Cargo

讓我們開始轉換 Hello World 程式到 Cargo。
要 Cargo 化專案的話，你需要做以下三件事：

1. 把你的原始碼檔案放到正確的目錄。
2. 去除舊的執行檔（在 Windows 是 `main.exe`，其他則是 `main`），
   並且建立一個新的。
3. 建立 Cargo 組態 (configuration) 檔。

讓我們開始吧！

### 建立新的執行檔和原始碼目錄

首先，回到你的終端機，移動你的 *hello_world* 目錄，輸入以下指令：

```bash
$ mkdir src
$ mv main.rs src/main.rs
$ rm main  # or 'del main.exe' on Windows
```

Cargo 預期你的原始碼會放在 *src* 目錄內，所以我們先做這個。
最上層的專案目錄（在此為 *hello_world*）保留來放置 README 檔、授權資訊、及其他跟你的程式碼無關的東西。
這樣可以讓你保持專案的整潔。
物有所屬，所有東西都有自己的家。

然後，複製 *main.rs* 到 *src* 目錄，然後刪除 `rustc` 編譯出的檔案。通常來說， `main` 在 Windows 下會被 `main.exe` 取代。

這個例子把 `main.rs` 作為原始碼檔案保留下來，因為它可以簡歷執行檔。
如果你想要建立一個函式庫 (library)，你應該把檔案命名為 `lib.rs`。
Cargo 使用這樣的慣例去編譯你的專案，但是如果你想要的話，你還是可以更改它。

### 建立組態檔

接著，在 *hello_world* 目錄下建立一個新的檔案，命名為 `Cargo.toml`。

確保 `Cargo.toml` 的 `C` 是大寫，否則 Cargo 會無法處理這樣的組態檔。

這個檔案使用 *[TOML]* (Tom's Obvious, Minimal Language) 格式。
TOML 跟 INI 很類似，但是有些額外的好東西，而且被用來作為 Cargo 的組態格式。

[TOML]: https://github.com/toml-lang/toml

在檔案內，輸入以下資訊：

```toml
[package]

name = "hello_world"
version = "0.1.0"
authors = [ "Your name <you@example.com>" ]
```

第一行，`[package]` 指出以下的陳述是用來配置一個套件 (package)。
當我們要加入更多資訊到這個檔案內，我們會增加其他的小節 (sections)，但是現在，我們只有套件組態的設定。

其他三行設定了三項 Cargo 編譯程式所需要知道的組態：程式的名字、它的版本、和誰是作者。

當你加入了這些資訊到 *Cargo.toml* 檔案內後，存檔然後結束。

## 建立並執行 Cargo 專案

當你的 *Cargo.toml* 檔案被放在專案的根目錄後，你應該準備好要建立並執行你的 Hello World 程式了！
輸入以下指令：

```bash
$ cargo build
   Compiling hello_world v0.1.0 (file:///home/yourname/projects/hello_world)
$ ./target/debug/hello_world
Hello, world!
```

蹦！如果一切順利，`Hello, world!` 應該再次印在終端機上了。

你可以透過 `cargo build` 建置專案、且透過 `./target/debug/hello_world` 執行它，但你其實可以直接以 `cargo run` 一步執行兩者：

```bash
$ cargo run
     Running `target/debug/hello_world`
Hello, world!
```

請注意，這個範例沒有重新建置專案。
Cargo 判斷檔案沒有更動，所以他直接執行執行擋。
如果你有修改你的原始碼，Cargo 會在執行前重新建置專案，然後你會看到：

```bash
$ cargo run
   Compiling hello_world v0.1.0 (file:///home/yourname/projects/hello_world)
     Running `target/debug/hello_world`
Hello, world!
```

Cargo 會檢查是否專案內的檔案有被更改，而且只會在專案有更動的時候重新建置。

在簡單的專案中，Cargo 無法比 `rustc` 帶來更多好處，但是它在未來會越來越有用。
在用到許多 crates 的複雜專案中，使用 Cargo 去協調建置會比較簡單。
你只需要執行 `cargo build`，然後一切都會正確的運行。

## 建立發行版

當你的專案最終準備好要發行，你應該使用 `cargo build --release` 來最佳化編譯你的專案。
這些最佳化讓你的 Rust 程式碼執行得更快，但是會讓你的程式編譯起來多花點時間。
這也是為什麼會有兩種不同的 profiles，一個用於開發，一個用於建置最終給使用者的程式。

執行這個指令同時會讓 Cargo 建立一個新的檔案叫做 *Cargo.lock*，檔案看起來像這樣：

```toml
[root]
name = "hello_world"
version = "0.1.0"
```

Cargo 使用 *Cargo.lock* 去追蹤你的應用程式的依賴關係。
這是 Hello World 專案的 *Cargo.lock* 檔。
這個專案沒有任何依賴關係，所以檔案有點稀疏。
實際上，你不需要自己去碰這個檔案；只要讓 Cargo 去處理就好了。

就這樣！如果你一路照著做到現在，你應該已經成功的以 Cargo 建置 `hello_world` 了。

即使這個專案很簡單，它也使用了許多之後你的 Rust 生涯中會真實用上的工具。
事實上，你可以預期，幾乎所有的 Rust 專案都會透過類似以下的指令開始：

```bash
$ git clone someurl.com/foo
$ cd foo
$ cargo build
```

## 簡單的開始一個新 Cargo 專案

當你想要開始一個新專案的時候，你不需要每次都重新執行一遍前面的流程！
Cargo 可以快速的建立專案目錄的骨架，然後你就可以開始開發。

用 Cargo 開始一個新專案，只要輸入 `cargo new`：

```bash
$ cargo new hello_world --bin
```

這個指令傳遞了 `--bin` 因為他的目的是直接建議一個可執行的應用程式，而不是函式庫 (library)。
執行擋也常被稱作 *binaries*。

Cargo 產生兩個檔案和一個目錄給我們：`Cargo.toml` 和內含 *main.rs* 的 *src* 目錄。
他們看起來與我們前面手動建立的很像。

這些就是我們全部所需要開始的東西。
首先，打開 `Cargo.toml`。
它應該看起來像這樣：

```toml
[package]

name = "hello_world"
version = "0.1.0"
authors = ["Your Name <you@example.com>"]
```

Cargo 會根據你給它的參數和你的 `git` 環境組態產生有合理預設值的 `Cargo.toml`。
而且你能注意到 Cargo 同時也把 `hello_world` 目錄初始化成 `git` 的 repository。

至於 `src/main.rs` 內應該會像這樣：

```rust
fn main() {
    println!("Hello, world!");
}
```

Cargo 會幫你產生 "Hello World!"，你就可以準備開始寫程式了！

> 註：如果你想要閱覽更多 Cargo 的細節，可以查閱官方的[Cargo 指南][Cargo guide]，其中包含有所有的功能。

[Cargo guide]: http://doc.crates.io/guide.html
