# 10. Environment, Secrets ve Security

`env.get name`, environment value döndürür; yoksa `nothing`. Dotenv-style değerler source directory çevresinden yüklenir; process environment dotenv değerinin önüne geçer. Quoted ve unquoted değerler desteklenir.

`secrets.get name` secret wrapper veya `nothing`; `secrets.require name` ise yoksa error döndürür.

Secret wrapper display, string conversion, interpolation, nested list/object representation ve diagnostic text içinde gerçek değeri göstermeyip `[REDACTED]` üretir. Secret'i göstermek yerine supported runtime operation'a doğrudan geçirmek gerekir.

`janna new` tarafından oluşturulan `.gitignore`, `.env` ve `.env.*` dosyalarını ignore eder, `.env.example` için istisna bırakır. Release packaging sensitive `.env` dosyalarını kopyalamaz ve final output'ta yeniden tarar; bulursa packaging durur. Build testleri de local `.env` dosyasının app içine embed edilmediğini doğrular.

