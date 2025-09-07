# 🔎 Git Merge ve Rebase Farkı (Temel Mantık)

* Merge: İki branch’i birleştirir → commit geçmişi **branch’ler birleşmiş olarak kalır**.
* Rebase: Senin branch’ini **başka bir branch’in en sonuna “taşır”**, commit geçmişini **daha düz ve temiz** yapar.

### Senaryo

1. `main` branch’inde 2 commit var: `A` ve `B`.
2. Sen `feature-login` branch’ini `B`’den oluşturup 2 commit yaptın: `C` ve `D`.
3. Bu sırada `main` branch’ine 1 commit daha geldi: `E`.

```
main:  A -- B -- E
feature-login:   B -- C -- D
```

* Eğer **merge** yaparsan:

```
A -- B -- E ---- M
      \       /
       C -- D
```

M → Merge commit.

* Eğer **rebase** yaparsan:

```
A -- B -- E -- C' -- D'
```

Yani senin commit’lerin (`C`, `D`) sanki `E`’den sonra yapılmış gibi yeniden yazılır.

---

### 🔑 Avantajlar

* Commit geçmişi **daha temiz** olur.
* Özellikle ekip projelerinde “feature branch’ler main’e gömülmeden önce rebase edilir”, böylece merge commit’leri çoğalmaz.