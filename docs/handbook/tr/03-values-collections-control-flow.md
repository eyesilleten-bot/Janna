# 3. Değerler, Koleksiyonlar ve Kontrol Akışı

## 3.1 Listeler

```janna
numbers is [10, 20, 30]
show count of numbers
show first of numbers
show last of numbers
add 40 to numbers
remove 20 from numbers
```

`count of`, `first of`, `last of` expression'dır. `add ... to ...` ve `remove ... from ...` isimlendirilmiş bir listeyi değiştirir.

## 3.2 Object'ler

```janna
player is
    name is "Ege"
    level is 1
    stats is
        score is 100
```

Property'ler dotted access ile okunur ve dotted path üzerinden atanabilir.

```janna
show player.name
player.stats.score is 150
increase player.level by 1
```

## 3.3 Koşullu akış

```janna
when score is above 90
    show "Yüksek"
otherwise when score is at least 50
    show "Orta"
otherwise
    show "Düşük"
```

## 3.4 Döngüler

`repeat`, `repeat forever`, `while` ve `each` desteklenir. `stop` aktif döngüyü bitirir; `skip` sonraki iterasyona geçer.

## 3.5 Mutation

`increase target by value` ve `decrease target by value`, değişkenler ve dotted property path'leri üzerinde çalışır ve runtime'da sayısal değerler gerektirir.

## 3.6 Membership ve mantık

Koşullarda `is in`, `is not in`, `and`, `or` ve `not` kullanılabilir.

