# 2. Syntax Katmanları

Janna V3'te birbiriyle ilişkili üç syntax katmanı vardır: Canonical Janna, Keyboard Shorthand ve AlienJanna rendering.

## 2.1 Canonical Janna

Canonical syntax, shorthand normalizasyonundan sonra parser'ın gördüğü temel dil biçimidir.

```janna
use text
name is "Ege"
when score is above 10
    show name
```

## 2.2 Keyboard Shorthand

Keyboard Shorthand ASCII kaynak syntax'ıdır. Lexer, parsing öncesinde bunu canonical biçime normalize eder; dolayısıyla shorthand ve canonical kod aynı parser/runtime semantiğini kullanır. Tırnak içindeki string'ler dönüşümden korunur.

| Shorthand | Canonical |
|---|---|
| `+text` | `use text` |
| `name := "Ege"` | `name is "Ege"` |
| `name = "Ege"` | `name is "Ege"` |
| `-> name` veya `>> name` | `show name` |
| `? score > 10` | `when score is above 10` |
| `?? score >= 5` | `otherwise when score is at least 5` |
| `:` | `otherwise` |
| `@5` | `repeat 5` |
| `@forever` | `repeat forever` |
| `@ item : items` | `each item in items` |
| `health += 5` | `increase health by 5` |
| `health -= 2` | `decrease health by 2` |
| `push value to items` | `add value to items` |
| `len / first / last` | `count of / first of / last of` |
| `input` | `ask` |
| `for` | `each` |
| `import` | `use` |
| `try / catch` | `attempt / if fails` |
| `assert` | `expect` |
| `fn / return` | `task / give` |
| `break / continue` | `stop / skip` |
| `if / else if / else` | `when / otherwise when / otherwise` |
| `== != > < >= <=` | canonical comparison sözlüğü |
| `&& || !` | `and or not` |
| `true false null` | `yes no nothing` |

## 2.3 AlienJanna rendering

AlienJanna şu anda ayrı bir parser modu değil, deterministic bir **presentation/rendering katmanıdır**. `render_alien_source`, önce Keyboard Shorthand'i normalize eder; sonra canonical ifadeleri sembolik biçimde render eder. Indentation, boş satırlar, yorumlar ve asıl kaynak dosya değişmeden kalır.

Bu source snapshot'ındaki renderer gerçekten ASCII `?` tabanlı semboller kullanır; `alien_syntax.py` içinde gizli non-ASCII glyph yoktur.

Önemli: Şu anda `.ja` dosyasını doğrudan AlienJanna kaynak modu olarak çalıştıran public bir CLI/editor switch'i yoktur. Runtime `alien_syntax` capability'sini bildirir çünkü rendering katmanı mevcuttur; normal execution yine normalize edilmiş/canonical Janna üzerinden gider.

