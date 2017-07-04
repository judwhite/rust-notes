## Rust Notes

`rustc 1.9.0 (e4e8b6668 2016-05-18)`

Installation:
- Install with rustup - https://www.rustup.rs/

IDEs:
- IntelliJ - works pretty good with Rust plugin. No debugging.
- VSCode - haven't tested, supposedly has debugging. May need additional plugin "racer".
- Visual Studio - Rust plugin doesn't work with crates (packages), makes it basically unusable
- Latest info: https://areweideyet.com/

Learning Resources:
- TRPL: https://doc.rust-lang.org/book/second-edition/ch01-00-introduction.html
- Cargo guide: http://doc.crates.io/guide.html
- 24 days of Rust: http://zsiciarz.github.io/24daysofrust
- Rusty by Example: https://rustbyexample.com/
- Rust Guidelines / Idioms: http://aturon.github.io
- https://github.com/brianquinlan/learn-rust

Community:
- IRC: irc.mozilla.org:6667 #rust, #rust-beginners, #cargo
- Forum: https://users.rust-lang.org/

Blog posts:
- http://neikos.me/Using_Stainless_with_Rocket.html
- https://gsquire.github.io/static/post/rest-in-rust/
- http://hermanradtke.com/2016/05/23/connecting-webservice-database-rust.html
- https://dfockler.github.io/2016/05/20/web-server.html
- http://hermanradtke.com/2016/05/16/creating-a-basic-webservice-in-rust.html
- https://auth0.com/blog/2015/11/30/build-an-api-in-rust-with-jwt-authentication-using-nickelrs/

Useful macros:
- https://doc.rust-lang.org/std/#macros

Error handling:
- https://doc.rust-lang.org/book/second-edition/ch09-00-error-handling.html
- http://blog.burntsushi.net/rust-error-handling/
- Stack trace: https://crates.io/crates/backtrace

Common data structures:
- Vectors (lists):
  - https://doc.rust-lang.org/stable/book/second-edition/ch08-01-vectors.html
  - https://doc.rust-lang.org/1.4.0/std/vec/struct.Vec.html
- HashMap (dictionary, map, key/value):
  - https://doc.rust-lang.org/book/second-edition/ch08-03-hash-maps.html
  - https://doc.rust-lang.org/std/collections/struct.HashMap.html

rustfmt:
- Currently in a transitional phase; this is a bit painful
- `rustup install nightly`
- `rustup default nightly` (optional?)
- `cargo install rustfmt-nightly`
- (on Windows) Copy necessary DLL's from `C:\Users\[user_name]\.rustup\toolchains\nightly-x86_64-pc-windows-msvc\lib\rustlib\x86_64-pc-windows-msvc\lib`
  to `C:\Users\[user_name]\.cargo\bin`
- `rustup default stable`
- If this doesn't work consult the docs https://github.com/rust-lang-nursery/rustfmt

Linters:
- Clippy:
  - `cargo install clippy` (requires nightly)
  - `cargo clippy`

Testing:
- Name file `lib.rs` (for libs only? TODO), or put in ./tests directory. When using ./tests, each .rs file is treated as an individual crate.
- Test function attribute: `#[test]`
- `#[cfg(test)] mod tests { use super::*; #[test] fn my_test() { ... } }`
- `#[cfg(test)]` prevents tests from becoming part of the normal binary.
- Assert macro: `assert_eq!`
- https://doc.rust-lang.org/1.12.1/book/testing.html
- https://doc.rust-lang.org/stable/book/second-edition/ch11-00-testing.html
- Code coverage: https://users.rust-lang.org/t/tutorial-how-to-collect-test-coverages-for-rust-project/650 (kcov)

Benchmarking:
- Unstable feature
- `rustup default nightly`
- Add #![feature(test)] to top of lib.rs to enable
- `extern crate test;`
- `use test::Bencher;`
- `#[bench] fn bench_something(b: &mut Bencher) { b.iter(|| your_function()); }`
- `cargo bench` or `rustup run nightly cargo bench`
- https://doc.rust-lang.org/1.12.1/book/benchmark-tests.html
- https://github.com/BurntSushi/cargo-benchcmp
- Can run on stable? https://crates.io/crates/bencher

Fuzz Testing:
- https://rust-fuzz.github.io/book/cargo-fuzz.html
- https://rust-fuzz.github.io/book/afl.html
- https://github.com/rust-fuzz/afl.rs

Randomized Testing:
- https://github.com/BurntSushi/quickcheck

Profiling:
- https://www.suchin.co/2016/05/11/Introducing-Cargo-Profiler/
- http://athemathmo.github.io/2016/09/14/tools-for-profiling-rust.html
- http://blog.adamperry.me/rust/2016/07/24/profiling-rust-perf-flamegraph/
- https://dev.to/martincerny/profiling-rust-code-on-windows-using-codexl

Mocking:
- API mocking: https://github.com/jmatraszek/haxonite

Command line parsing:
- https://crates.io/crates/docopt

Serialization:
- JSON:
  - https://github.com/serde-rs/json
  - http://www.arewewebyet.org/topics/json/
- XML: https://crates.io/crates/xml-rs
- Protobuf:
  - https://github.com/stepancheg/rust-protobuf
  - https://github.com/dflemstr/rq/tree/master/serde-protobuf
- BSON: https://github.com/zonyitoo/bson-rs
- YAML: https://github.com/dtolnay/serde-yaml
- TOML: https://github.com/alexcrichton/toml-rs
- Serde (generic serialization framework):
  - http://zsiciarz.github.io/24daysofrust/book/vol2/day8.html
  
Encoding:
- http://www.arewewebyet.org/topics/encoding/

Windows Service:
- https://github.com/bozaro/daemon-rs

Windows:
- Windows Registry: https://github.com/gentoo90/winreg-rs
- Win32 API:
  - https://crates.io/crates/winapi
  - https://crates.io/crates/kernel32-sys
  - https://crates.io/keywords/win32

Databases:
- SQL Server: https://github.com/steffengy/tiberius
- Postgres:
  - https://crates.io/crates/postgres
  - http://zsiciarz.github.io/24daysofrust/book/vol1/day11.html
- ODBC:
  - https://github.com/pacman82/odbc-sys
  - https://github.com/Koka/odbc-rs
- Redis:
  - http://zsiciarz.github.io/24daysofrust/book/vol1/day18.html
  - https://crates.io/crates/redis
- RocksDB: https://crates.io/crates/rocks
- MySQL: https://crates.io/crates/mysql
- SQLite: https://crates.io/crates/rusqlite
- LMDB: https://crates.io/crates/lmdb-rs
- Kafka: https://crates.io/crates/kafka
- ElasticSearch: https://crates.io/crates/rs-es
- CSV:
  - https://docs.rs/csv/1.0.0-beta.3/csv/
  - http://zsiciarz.github.io/24daysofrust/book/vol1/day3.html
  - https://github.com/BurntSushi/rust-csv
- http://www.arewewebyet.org/topics/database/#drivers

Logging/Metrics:
- Standard: https://doc.rust-lang.org/log/log/index.html
- Structured: https://github.com/slog-rs/slog
- Prometheus: https://github.com/pingcap/rust-prometheus
- http://www.arewewebyet.org/topics/logging/

HTTP:
- https://github.com/hyperium/hyper
- http://zsiciarz.github.io/24daysofrust/book/vol1/day5.html
- http://www.arewewebyet.org/topics/stack/
- HTTP/2: https://crates.io/crates/solicit
- https://crates.io/crates/cookie
- https://crates.io/crates/frank_jwt
- https://crates.io/crates/urlparse

Templating:
- http://www.arewewebyet.org/topics/templating/

SOAP:
- https://www.reddit.com/r/rust/comments/4dlbgx/wsdl_services/
- https://github.com/jaxx/wsdl-rs

File system access:
- Reading: https://doc.rust-lang.org/stable/book/second-edition/ch12-02-reading-a-file.html
- https://rustbyexample.com/std_misc/file/open.html
- https://rustbyexample.com/std_misc/file/create.html
- Filesystem Operations: https://rustbyexample.com/std_misc/fs.html

Crypto/TLS/SSH:
- https://github.com/DaGenix/rust-crypto/
- NaCl: https://crates.io/crates/libsodium-sys
- TLS: https://crates.io/crates/rustls
- OpenSSL: https://crates.io/crates/openssl
- SSH: https://crates.io/search?q=ssh
- http://www.arewewebyet.org/topics/crypto/

Compression:
- Gzip: https://crates.io/crates/flate2
- Snappy:
  - https://github.com/JeffBelgum/rust-snappy
  - https://github.com/BurntSushi/rust-snappy
- LZW: https://github.com/nwin/lzw
- LZMA: https://crates.io/crates/rust-lzma
- http://www.arewewebyet.org/topics/compression/

Hashing:
- crc32: https://crates.io/crates/crc
- md5: https://crates.io/crates/md5
- sha1: https://crates.io/crates/sha1
- sha256/512: https://raw.githubusercontent.com/DaGenix/rust-crypto/master/src/sha3.rs
- murmur3: https://crates.io/crates/murmur3
- murmurhash2 (64-bit): https://crates.io/crates/murmurhash64
- bcrypt: https://crates.io/crates/bcrypt

Email:
- http://www.arewewebyet.org/topics/email/
- https://crates.io/crates/lettre
- http://zsiciarz.github.io/24daysofrust/book/vol2/day22.html

Other:
- Cuckoo Filter (set membership, like a Bloom Filter): https://crates.io/crates/cuckoofilter
- SQL AST: https://github.com/OsnaCS/uosql-server/blob/master/server/src/parse/ast.rs
- Child processes: https://rustbyexample.com/std_misc/process.html
- Command Line Argument Parsing (CLAP):
  - http://zsiciarz.github.io/24daysofrust/book/vol2/day12.html
  - https://github.com/kbknapp/clap-rs

Regex:
- https://doc.rust-lang.org/regex/regex/index.html
- https://crates.io/crates/regex

Concurrency:
- https://doc.rust-lang.org/stable/book/second-edition/ch16-00-concurrency.html
- https://doc.rust-lang.org/stable/book/first-edition/concurrency.html

DNS:
- https://crates.io/crates/trust-dns
- https://crates.io/keywords/dns

TCP:
- https://users.rust-lang.org/t/how-to-write-a-simple-tcp-client-and-server/3712/2
- https://stackoverflow.com/questions/17445485/example-tcp-server-written-in-rust
- https://nbaksalyar.github.io/2015/07/10/writing-chat-in-rust.html#tcp-server
- https://doc.rust-lang.org/std/net/struct.TcpListener.html
- https://doc.rust-lang.org/std/net/struct.TcpStream.html

Futures/Async:
- https://tokio.rs/
- https://docs.rs/futures/0.1.14/futures/
- https://github.com/nikomatsakis/rayon

Signal handling:
- https://github.com/BurntSushi/chan-signal
- https://github.com/rust-lang/rfcs/issues/1368

Environment variables:
- `use std::env;`
- `env::var("ENV_VAR_NAME")`
- http://zsiciarz.github.io/24daysofrust/book/vol2/day5.html
