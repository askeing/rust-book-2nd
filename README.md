# Rust 程式語言

這是 "Rust 程式語言" 的下一版，當前版本的書放在 [Rust repository 中][src]。
如果你想要閱讀那一本書，你應該從那邊或[此網頁][prod]去一探究竟。

[src]: https://github.com/rust-lang/rust/tree/master/src/doc/book
[prod]: https://doc.rust-lang.org/book/

如果你想瀏覽這一版本，它放在 [Github pages][html] 上。

[html]: http://rust-lang.github.io/book/

## 需求

建置這本書需要 [mdBook]。透過以下指令可以安裝：

[mdBook]: https://github.com/azerupi/mdBook

```bash
$ cargo install mdbook
```

## 建置

建置書籍，輸入：

```bash
$ mdbook build
```

輸出的結果將會被放在 `book` 的子目錄下。
如果想瀏覽結果，只需要在你的瀏覽器打開就可以了：

```bash
$ firefox book/index.html
```

執行測試：

```bash
$ mdbook test
```

> 譯註：以下維持原文，不做翻譯。

## Contributing

I’m not going to be accepting major changes at first, but pull requests to fix
typos and such are welcome. Please file any issues for any bugs you find, and
utilize the issue tagged with `Discussion` to raise any larger questions /
feedback.

This repository is under the same license as Rust itself, MIT/Apache2.

There are a number of labels on Issues:

* `Discussion` issues are for discussing the chapters. There’s an issue per
  section.
* `Bug` issues indicate problems in the text.
* `Needs Backport` will be used when we are further along. At some point, we
  will import the text into their review system, and so changes made here will
  need to be upstreamed. This will track those.

Finally, there’s the `S-` labels, which are for various ‘status’es:

* `S-initial`: Steve has not done any work here yet.
* `S-rough-draft`: Steve has worked up a rough draft of what this section will
  look like.
* `S-under-review`: Aaron and Steve are in the process of reviewing this
  section.
* `S-done`: imported into No Starch’s system. There may still be changes based
  on their feedback, even after a section is marked `S-done`.

## No Starch

As the book will be published by No Starch, we first iterate here, then ship the
text off to No Starch. Then they do editing, and we fold it back in.

As such, there’s a directory, `nostarch`, which corresponds to the `S-done`,
and its current status in No Starch’s system.
