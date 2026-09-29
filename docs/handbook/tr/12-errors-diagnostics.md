# 12. Errors ve Diagnostics

Syntax errors; invalid indentation, malformed expression, eksik block, invalid identifier, malformed object/test veya incomplete `attempt` gibi durumları kapsar ve mümkün olduğunda line number verir.

Runtime errors; unknown variable/task/action, yanlış argument sayısı veya type, invalid path/schema, missing required secret, HTTP/AI option hatası, illegal job transition ve division by zero gibi durumları kapsar.

V3 capabilities içinde `source_locations` ve `task_trace` bulunur. Error'lar execution path uygunsa source-file ve task/module context'i ile zenginleştirilir. Circular imports açıkça algılanır.

CLI expected Janna error'larını user-facing biçimde basıp normalde exit code 1 döndürür. `runtime.exit` ayrı ele alınır ve istenen 0–255 kodunu döndürür. Unexpected internal exception normal user'a Python traceback dökmek yerine CLI boundary'sinde genel internal-problem mesajına çevrilir.

Registered secret değerleri diagnostic text içinde de redacted tutulur.

