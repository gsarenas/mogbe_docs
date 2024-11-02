# mogbe_docs
Repositório dedicado à documentação do robô MOGBE.

## Passos para reprodução (build)

Criar um diretório `docs`

```bash
mkdir docs && cd docs
```

Clonar o repositório `mogbe_docs` dentro de `docs`:

```bash
git clone git@github.com:gsarenas/mogbe_docs.git
```

```bash
git clone https://github.com/gsarenas/mogbe_docs.git
```

Rodar o `sphinx-quickstart` para gerar o `Makefile`:

```bash
sphinx-quickstart
```

> Durante os prompts, é importante selecionar `y` quando perguntado se quer diretórios separados para `source` e `build`

Após gerar tudo, basta alterar o caminho no Makefile the `source` para `mogbe_docs` na variável `SOURCEDIR`

Para compilar tudo, rode:

```bash
make html
```

Para gerar uma nova build, exclua os arquivos em cache:

```bash
make clean
```

E repita o comando de build:

```bash
make html
```

<!--

CHEATSHEET:

```{note} Notes require **no** arguments, so content can start here.
```

```{admonition} Nota adm
This is my note
```

```{admonition} Nota
---
class: note
---
Uma nota
```

```{admonition} Dica tip
---
class: tip
---
Uma dica tip
```

```{admonition} Atenção
---
class: attention
---
Uma atenção
```

```{admonition} Cuidado
---
class: caution
---
Um cuidado
```

```{admonition} Perigo
---
class: danger
---
Um perigo
```

```{admonition} Erro
---
class: error
---
Um erro
```

```{admonition} Dica hint
---
class: hint
---
Uma dica hint
```

```{admonition} Importante
---
class: important
---
Um importante
```

```{admonition} Saiba mais
---
class: seealso
---
Um saiba mais
```

```{admonition} Aviso
---
class: warning
---
Um aviso
```

-->