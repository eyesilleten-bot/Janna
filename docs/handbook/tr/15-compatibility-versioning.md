# 15. Compatibility ve Versioning

V3 automated compatibility testleri üç public surface'i sabitler: CLI primary commands/aliases, built-in module adları ve `runtime.capabilities` isimleri.

Bu freeze gelecekte özellik eklenemeyeceği anlamına gelmez. Ancak mevcut public surface'in kaldırılması veya incompatible rename edilmesi bilinçli bir compatibility değişikliği olarak ele alınmalıdır.

`runtime.generation` bu snapshot'ta `3`tür. `version.py`; release version `0.3.0`, channel `release`, görünen version `0.3.0` tanımlar. Final release switch yapıldığında release-facing dokümantasyon final value ile yeniden kontrol edilmelidir.

Bu Handbook yaşayan dokümandır. V4/V5 aynı feature family'ye ait yenilikleri mevcut bölüme eklemeli; yalnız gerçekten yeni public subsystem için yeni numbered section açılmalıdır. Source ve regression tests, dokümantasyonla çelişki olduğunda final source of truth'tur.

