# 1. Dil Temelleri

Janna, okunabilir ifadeler üzerine kurulu indentation tabanlı bir programlama dilidir. Komut satırı aracı `.ja` kaynak dosyalarını kabul eder. Kaynak UTF-8 olarak okunur; dosya başındaki UTF-8 BOM kabul edilir. Boş satırlar yok sayılır ve ilk boşluk olmayan karakteri `#` olan satırlar yorumdur.

## 1.1 İlk program

```janna
name is "Ege"
show "Merhaba {name}"
```

`is` bir değer atar. `show` bir expression'ı gösterir. String interpolation, string içinde `{name}` biçimini kullanır.

## 1.2 Indentation

Bloklar indentation ile tanımlanır. Tab karakterleri reddedilir. Her blok seviyesi tam dört boşluktur.

```janna
repeat 3
    show "Merhaba"
```

## 1.3 Değerler

Canonical Janna literal'ları; text, tam sayı, ondalık sayı, `yes`, `no` ve `nothing` içerir.

```janna
message is "Merhaba"
count is 10
ratio is 1.5
ready is yes
finished is no
result is nothing
```

Keyboard Shorthand ayrıca `true`, `false` ve `null` kabul eder; bunlar parsing öncesinde `yes`, `no` ve `nothing` biçimine normalize edilir.

## 1.4 Expression'lar

Aritmetik `+`, `-`, `*`, `/`, `%`, unary minus ve parantezleri destekler. Çarpma, bölme ve modulo; toplama ve çıkarmadan önce uygulanır.

## 1.5 Koşullar

Canonical karşılaştırma sözlüğü: `is`, `is not`, `is above`, `is below`, `is at least`, `is at most`, `is in`, `is not in`. Koşullar `and`, `or` ve `not` ile birleştirilebilir. Tek başına kullanılan bir değer koşul içinde `yes` ile karşılaştırılır.

```janna
when age is at least 18 and ready
    show "Hazır"
otherwise
    show "Hazır değil"
```

## 1.6 Girdi ve çıktı

```janna
name is ask "Ad: "
show "Merhaba {name}"
```

## 1.7 Temel statement aileleri

Temel statement'lar `use`, `show`, `is` ile assignment, `when`, `otherwise when`, `otherwise`, `repeat`, `repeat forever`, `while`, `each`, `add`, `remove`, `increase`, `decrease`, `task`, `give`, `attempt`, `if fails`, `test`, `expect`, `stop` ve `skip` ailelerini içerir. Ayrıntılı bağlamları ilerleyen bölümlerdedir.

