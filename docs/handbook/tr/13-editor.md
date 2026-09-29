# 13. Janna Editor Beta

Repository'deki Janna language extension package'ı `janna-language` version `0.2.0`, publisher `eyesilleten-bot` olarak tanımlıdır. `janna-language-0.2.0.vsix` olarak package edilmiştir ve VS Code-compatible editor'lerde, örneğin Cursor'da, kurulabilir.

Editor `.ja` ve `.janna` dosyalarını Janna language olarak tanır. CLI run/check/build tarafı şu anda `.ja` ister; bu nedenle portable project source extension'ı `.ja`dır.

Beta sekiz command sunar: `Janna: Run`, `Check`, `Test`, `Build`, ayrıca `Run Project`, `Check Project`, `Test Project`, `Build Project`.

`janna.developmentEnginePath`, development sırasında optional `janna.py` yolu belirlemek için kullanılabilir.

Editor ayrı bir runtime/compiler değildir; command integration ve language support katmanıdır. Execution ve validation Janna CLI/runtime tarafından yapılır.

