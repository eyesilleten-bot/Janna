# 14. SDK, Packaging ve Installation

V3 Windows SDK; `janna.exe`, `ja.cmd` ve private `builder_runtime` içerir. Builder runtime, son kullanıcının ayrı Python development toolchain kurmasına gerek kalmadan `janna build` için gereken runtime/engine parçalarını taşır.

Release package SDK'yı, README/Quickstart dosyalarını, Editor Beta VSIX'ini, examples'ı ve install/uninstall scriptlerini içerir. Sensitive `.env` dosyaları release output'tan filtrelenir ve final scan ile kontrol edilir.

Inno Setup installer current user's Local AppData `Programs\Janna` dizinine kurulum yapar, Janna klasörünü user PATH'e ekler ve admin privilege gerektirmeyecek şekilde `PrivilegesRequired=lowest` kullanır.

Yeni terminal oturumunda `janna version`, `janna help` ve `ja app.ja` kullanılabilir.

Built Janna application, `dist\<app>.exe` altında one-file Windows executable'dır; bundled user module'ler ve root app identity/arguments davranışı korunur.

