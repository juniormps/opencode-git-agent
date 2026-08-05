# Installation

Este guia explica como instalar o OpenCode Professional Git Agent.

## Pré-requisitos

Antes de começar, verifique se você possui:

- Git instalado
- OpenCode instalado
- Linux, macOS ou WSL (Windows)

Confira as versões:

```bash
git --version
opencode --version
```

---

## Clonando o repositório

```bash
git clone https://github.com/SEU-USUARIO/opencode-git-agent.git

cd opencode-git-agent
```

---

## Criando as pastas do OpenCode

Caso elas ainda não existam:

```bash
mkdir -p ~/.config/opencode/agents
mkdir -p ~/.config/opencode/commands
```

---

## Instalando o agente

Copie o agente:

```bash
cp agents/git-commit.md ~/.config/opencode/agents/
```

Copie o comando:

```bash
cp commands/commit.md ~/.config/opencode/commands/
```

---

## Verificando a instalação

Confira se os arquivos foram copiados:

```bash
ls ~/.config/opencode/agents

ls ~/.config/opencode/commands
```

Você deverá visualizar:

```
git-commit.md

commit.md
```

---

## Testando

Entre em qualquer repositório Git:

```bash
cd caminho/do/projeto
```

Abra o OpenCode:

```bash
opencode
```

Execute:

```text
/commit
```

Se tudo estiver correto, o agente irá:

- analisar as alterações;
- sugerir os commits;
- solicitar aprovação para o commit;
- solicitar aprovação para o push.

---

## Atualizando

Caso uma nova versão seja lançada:

```bash
git pull

cp agents/git-commit.md ~/.config/opencode/agents/

cp commands/commit.md ~/.config/opencode/commands/
```

---

## Desinstalando

Para remover o agente:

```bash
rm ~/.config/opencode/agents/git-commit.md

rm ~/.config/opencode/commands/commit.md
```

---

## Solução de problemas

### O comando `/commit` não aparece

Verifique se o arquivo está em:

```text
~/.config/opencode/commands/commit.md
```

---

### O agente não é encontrado

Confira:

```text
~/.config/opencode/agents/git-commit.md
```

---

### O OpenCode não inicia

Verifique a instalação:

```bash
opencode --version
```

---

## Suporte

Caso encontre algum problema, abra uma Issue neste repositório.
