# Customization Guide

Este documento explica como personalizar o comportamento do **OpenCode Professional Git Agent**.

---

# Estrutura

O projeto é composto por dois arquivos principais:

```
agents/
└── git-commit.md

commands/
└── commit.md
```

- `git-commit.md` contém todas as regras, permissões e comportamento do agente.
- `commit.md` define o comando `/commit`.

---

# Alterando o idioma

No arquivo:

```
agents/git-commit.md
```

localize:

```text
Responda sempre em português do Brasil.
```

Você pode alterar para:

```text
Always respond in English.
```

ou qualquer outro idioma.

---

# Alterando o padrão de mensagens

O agente utiliza **Conventional Commits**.

Exemplo:

```
feat(auth): adiciona autenticação JWT
```

Caso prefira mensagens tradicionais, substitua a seção:

```
## Padrão das mensagens
```

por sua convenção preferida.

Exemplo:

```
Adiciona autenticação JWT
```

---

# Permissões

As permissões ficam no início do arquivo:

```yaml
permission:
```

Exemplo:

```yaml
"git commit *": ask
```

Significados:

| Valor | Comportamento           |
| ----- | ----------------------- |
| allow | Executa automaticamente |
| ask   | Solicita aprovação      |
| deny  | Nunca executa           |

---

## Tornar commits automáticos

Altere:

```yaml
"git commit *": ask
```

para:

```yaml
"git commit *": allow
```

---

## Tornar push automático

**Não recomendado.**

Caso deseje:

```yaml
"git push": allow
"git push *": allow
```

---

## Bloquear completamente o push

```yaml
"git push": deny
"git push *": deny
```

---

# Alterando o comportamento do Git Add

Por padrão o agente evita:

```
git add .
```

e prepara apenas arquivos específicos.

Caso prefira adicionar tudo automaticamente,
modifique a seção:

```
## Segurança obrigatória
```

---

# Executando testes antes do commit

Você pode acrescentar no bloco:

```
## Procedimento
```

Exemplo:

```
Antes de preparar arquivos:

- execute npm test
- execute npm run lint
- execute npm run build

Caso algum comando falhe:

- informe o erro
- interrompa o commit
```

---

# Projetos React

Você pode especializar o agente adicionando:

```
Caso seja um projeto React:

- execute npm run lint
- execute npm run build
- somente continue se ambos terminarem com sucesso.
```

---

# Projetos Node.js

Adicione:

```
Caso seja um projeto Node.js:

- execute npm test
- execute npm run lint
```

---

# Projetos Python

```
Execute:

pytest

Somente continue caso todos os testes passem.
```

---

# Criando novos comandos

Os comandos ficam em:

```
commands/
```

Cada arquivo Markdown cria um comando.

Exemplo:

```
commands/

commit.md
review.md
release.md
deploy.md
```

Disponíveis no OpenCode como:

```
/commit

/review

/release

/deploy
```

---

# Criando novos agentes

Os agentes ficam em:

```
agents/
```

Exemplo:

```
agents/

git-commit.md
security.md
review.md
frontend.md
backend.md
docker.md
```

Podem ser chamados diretamente:

```
@git-commit

@review

@security
```

---

# Recomendações

É recomendado manter:

```
git commit -> ask

git push -> ask
```

Isso mantém o controle do usuário sobre qualquer alteração enviada ao repositório remoto.

---

# Segurança

Recomenda-se manter bloqueados:

- git reset
- git clean
- git rebase
- git merge
- git checkout
- git switch
- rm
- push --force

Esses comandos podem causar perda de trabalho caso utilizados automaticamente.

---

# Atualizando o agente

Após modificar os arquivos:

```
agents/git-commit.md

commands/commit.md
```

basta reiniciar o OpenCode.

Não é necessário reinstalar o agente.

---

# Contribuindo

Pull Requests são bem-vindos.

Ao contribuir:

- mantenha compatibilidade com OpenCode;
- preserve a segurança do agente;
- documente qualquer nova funcionalidade;
- atualize esta documentação sempre que necessário.
