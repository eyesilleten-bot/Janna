# 6. Dosyalar, Path'ler ve Dokümanlar

`use files` sonrasında şu actions kullanılabilir:

- `files.read path`
- `files.write path content`
- `files.append path content`
- `files.delete path`
- `files.exists path`
- `files.make_folder path`
- `files.list path`
- `files.delete_folder path` — yalnız boş klasörü siler.
- `files.join base child`
- `files.name path`
- `files.extension path`
- `files.parent path`
- `files.absolute path`
- `files.is_file path`
- `files.is_folder path`

`files.write_markdown path content` UTF-8 Markdown yazar.

`files.write_docx path content` `python-docx` üzerinden DOCX üretir; her input satırı bir paragraph olur. DOCX desteği installation'da yoksa runtime açık bir hata verir.

Bu özellik ailesi runtime capabilities içinde `document_output` ve `files_paths` olarak görünür ve check/run/build testleriyle kapsanır.

