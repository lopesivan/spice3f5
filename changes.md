
# remove o executável no índice e confirma
git add --chmod=-x caminho/do/arquivo
git commit -m "Remove executable bit"

# impede CRLF
git config core.autocrlf false


Boa! Se você quer **remover o bit de execução de todos os arquivos no repositório** (e registrar isso no Git), dá pra fazer de forma global.

### Passos:

1. **Remover a permissão de execução de todos os arquivos no diretório de trabalho:**

```bash
find . -type f -exec chmod -x {} +
```

2. **Dizer ao Git para marcar todos como “sem execução”:**

```bash
git ls-files -z | xargs -0 git add --chmod=-x
```

3. **Confirmar a mudança:**

```bash
git commit -m "Remove executable bit de todos os arquivos"
```

---

🔎 Dica: Se você quer só nos arquivos de código (por exemplo, `.c`, `.h`, `.txt`, `.md`), pode usar:

```bash
git ls-files '*.c' '*.h' '*.txt' '*.md' -z | xargs -0 git add --chmod=-x
```

---

Quer que eu te monte um comando que **mantém executável só scripts `.sh` e binários em `bin/`**, e remove dos demais automaticamente?


