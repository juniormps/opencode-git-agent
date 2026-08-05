# Contributing Guide

Obrigado por considerar contribuir com o **OpenCode Professional Git Agent**.

Toda contribuição é bem-vinda, seja corrigindo bugs, propondo melhorias, adicionando novos agentes ou aperfeiçoando a documentação.

---

# Como contribuir

Você pode contribuir de diversas formas:

- corrigindo bugs;
- sugerindo novas funcionalidades;
- melhorando a documentação;
- criando novos agentes;
- criando novos comandos;
- melhorando a segurança;
- aprimorando prompts e instruções;
- revisando Pull Requests.

---

# Antes de começar

Antes de desenvolver uma nova funcionalidade:

1. Verifique se já existe uma Issue relacionada.
2. Caso não exista, abra uma nova Issue descrevendo sua proposta.
3. Aguarde feedback antes de iniciar mudanças muito grandes.

Isso evita trabalho duplicado.

---

# Configurando o ambiente

Clone o projeto:

```bash
git clone https://github.com/SEU-USUARIO/opencode-git-agent.git

cd opencode-git-agent
```

Crie as pastas do OpenCode, caso necessário:

```bash
mkdir -p ~/.config/opencode/agents

mkdir -p ~/.config/opencode/commands
```

Copie os arquivos:

```bash
cp agents/git-commit.md ~/.config/opencode/agents/

cp commands/commit.md ~/.config/opencode/commands/
```

Teste a instalação:

```bash
opencode
```

Depois execute:

```text
/commit
```

---

# Fluxo recomendado

Crie uma branch para sua contribuição.

Exemplo:

```bash
git checkout -b feature/security-improvements
```

ou

```bash
git checkout -b docs/update-readme
```

Evite trabalhar diretamente na branch principal.

---

# Padrão de commits

Este projeto utiliza **Conventional Commits**.

Exemplos:

```text
feat(agent): adiciona suporte para múltiplos commits

fix(git): corrige detecção de arquivos sensíveis

docs(readme): melhora instruções de instalação

refactor(commands): reorganiza comando /commit
```

Tipos recomendados:

- feat
- fix
- docs
- refactor
- style
- test
- chore
- build
- ci
- perf
- revert

---

# Organização do código

## Agentes

Novos agentes devem ser adicionados em:

```
agents/
```

Exemplo:

```
agents/

git-commit.md

review.md

security.md

frontend.md
```

---

## Comandos

Novos comandos devem ser adicionados em:

```
commands/
```

Exemplo:

```
commands/

commit.md

review.md

release.md
```

Cada arquivo cria automaticamente um comando no OpenCode.

---

# Diretrizes para novos agentes

Sempre que possível, um agente deve:

- possuir um objetivo bem definido;
- evitar comportamentos destrutivos;
- solicitar aprovação para operações críticas;
- responder de forma consistente;
- seguir a documentação oficial do OpenCode.

---

# Segurança

Não envie Pull Requests que:

- removam verificações de segurança sem justificativa;
- permitam push automático por padrão;
- permitam reset automático;
- executem comandos destrutivos;
- exponham credenciais.

Mudanças relacionadas à segurança devem ser claramente documentadas.

---

# Documentação

Sempre que adicionar uma funcionalidade:

Atualize, quando necessário:

- README.md
- INSTALL.md
- CUSTOMIZATION.md
- SECURITY.md

A documentação deve permanecer sincronizada com o comportamento do projeto.

---

# Pull Requests

Ao abrir um Pull Request:

Descreva:

- objetivo da alteração;
- motivação;
- impacto esperado;
- capturas de tela (quando aplicável);
- possíveis incompatibilidades.

Evite Pull Requests muito grandes.

Prefira pequenas alterações focadas em um único objetivo.

---

# Issues

Ao abrir uma Issue, informe:

- sistema operacional;
- versão do OpenCode;
- versão do agente;
- descrição do problema;
- passos para reproduzir;
- comportamento esperado;
- comportamento observado.

Quanto mais detalhes, mais fácil será reproduzir o problema.

---

# Código de Conduta

Esperamos que todos mantenham um ambiente respeitoso.

Não serão tolerados:

- assédio;
- discriminação;
- ataques pessoais;
- linguagem ofensiva.

Discussões técnicas são bem-vindas quando conduzidas com respeito.

---

# Licença

Ao contribuir com este projeto, você concorda que sua contribuição será disponibilizada sob a mesma licença do projeto (MIT License).

---

# Obrigado!

Sua contribuição ajuda a tornar este projeto melhor para toda a comunidade.

Boas contribuições e bons commits! 🚀
