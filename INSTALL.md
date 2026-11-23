# Instalar a Prompt Elaboration

**Versão estável:** [v1.2](https://github.com/gubertaglia/prompt-elaboration/releases/tag/v1.2)  
**Download:** [prompt-elaboration-v1.2.zip](https://github.com/gubertaglia/prompt-elaboration/releases/download/v1.2/prompt-elaboration-v1.2.zip)

Este projeto contém **uma Agent Skill**, não um plugin, programa executável ou servidor MCP. O ZIP de release contém somente a pasta necessária para instalar a skill. O ZIP obtido por **Code → Download ZIP** contém o repositório inteiro e não deve ser confundido com o instalador.

## A. ChatGPT Web — enviar a skill nativa

Use este método quando sua conta exibir a função de upload de habilidades:

1. Baixe o ZIP da release **sem extrair**.
2. Acesse [chatgpt.com/skills](https://chatgpt.com/skills).
3. Escolha **Adicionar → Carregar do seu computador**.
4. Selecione `prompt-elaboration-v1.2.zip`.
5. Acompanhe a verificação da plataforma. Se aprovado, procure a habilidade em **Instaladas**.
6. Teste com um pedido de elaboração de prompt. Ela deve **gerar o prompt**, não executar a tarefa técnica descrita.

**Atenção:** a disponibilidade da opção depende do produto, plano, workspace e permissões. A plataforma poderá exigir análise ou bloquear um arquivo. A interface observada pelo mantenedor oferece a opção de carregamento, mas **isso ainda não comprova que este ZIP foi instalado com sucesso**.

Caso o recurso não esteja disponível, consulte [CHATGPT_WEB.md](CHATGPT_WEB.md) para reproduzir o fluxo em um Projeto. Projetos não equivalem à instalação nativa.

## B. Codex Desktop — instalar com Skill Installer

O Codex inclui a habilidade `$skill-installer`. No chat, selecione essa habilidade e peça:

```text
Instale a skill Prompt Elaboration do repositório
https://github.com/gubertaglia/prompt-elaboration
usando --ref v1.2 --path . --name prompt-elaboration.
Use o diretório de skills já reconhecido nesta instalação do Codex.
Não sobrescreva nenhuma outra skill.
```

O instalador oficial usa `--repo <owner>/<repo> --path <path>`, permite `--name` e instala em `$CODEX_HOME/skills` por padrão. A análise do seu código-fonte confirma que `--path .` aponta para a raiz, onde está o `SKILL.md`; `--name prompt-elaboration` impede usar `.` como nome de pasta. Esse caminho é **suportado pelo algoritmo**, mas a instalação específica no aplicativo do mantenedor ainda não foi testada.

**Nota de organização:** instalar a raiz por esse método pode copiar README e outros arquivos do repositório junto com a skill. Para instalar só `SKILL.md` e `agents/openai.yaml`, prefira o ZIP da release.

Se já existir uma pasta chamada `prompt-elaboration` no diretório de destino, o instalador oficial **interrompe sem sobrescrever**. Para atualizar, compare a versão instalada com a release e substitua somente essa pasta de modo consciente, preservando as demais.

## C. Codex Desktop — instalação manual do ZIP (Windows)

1. Baixe a release v1.2 e extraia o ZIP.
2. A pasta extraída deve se chamar `prompt-elaboration` e conter:

```text
prompt-elaboration/
├── SKILL.md
└── agents/
    └── openai.yaml
```

3. Copie **a pasta inteira** para o diretório pessoal de skills efetivamente reconhecido pelo seu Codex.
4. Exemplo de caminho que aparece na instalação do mantenedor: `%USERPROFILE%\.codex\skills\prompt-elaboration\SKILL.md`.
5. Abra uma nova conversa ou sessão se a lista não atualizar; digite `$prompt-elaboration` e confira a sugestão no seletor.

**Importante:** algumas versões/documentações também usam `%USERPROFILE%\.agents\skills`. Não duplique a skill em vários locais sem necessidade. O caminho válido é o identificado no aplicativo instalado, não uma regra universal.

## D. Teste funcional rápido

Após aparecer no seletor ou em habilidades instaladas, use uma missão simples:

```text
Elabore um prompt para investigar por que meu jogo Roblox perde FPS
quando acontecem muitas explosões simultâneas.
```

A resposta esperada inclui, conforme a interface e o pedido:
- Um **único prompt pronto para copiar**;
- Perguntas só se uma decisão relevante estiver faltando;
- Sugestões de configuração e de skills como `$rbx-optimize` somente quando apropriadas;
- **Nenhuma alteração no jogo** — a skill não deve executar a investigação solicitada;
- Nenhuma exigência automática de ciclos repetidos de testes no Studio; o prompt deve propor verificações pertinentes sem inventar resultados nem proibir medições necessárias.

A presença no seletor comprova descoberta, **não** que a skill funciona perfeitamente. O teste comportamental é uma verificação adicional.

## E. Problemas frequentes

| Sintoma | Verificação |
| --- | --- |
| Skill não aparece no Codex | Confira se existe `prompt-elaboration/SKILL.md` no diretório correto. Abra uma nova sessão. |
| Installer acusa destino existente | Não force sobrescrita. Confira a instalação anterior e substitua só essa pasta, se for uma atualização desejada. |
| ChatGPT não oferece upload | A função pode não estar disponível para a conta. Use temporariamente as instruções de Projeto em `CHATGPT_WEB.md`. |
| ChatGPT solicita análise ou bloqueia ZIP | Siga a avaliação da plataforma; não presuma que o arquivo será aceito. |
| Instalou em uma interface e não aparece na outra | As instalações **não precisam sincronizar** entre produtos. Instale separadamente. |
| Skill elabora e executa código ao mesmo tempo | Isso contradiz o objetivo definido no `SKILL.md`; registre o comportamento como possível falha para revisão. |

## F. Fontes verificadas

- [OpenAI — Skill Installer: instruções](https://github.com/openai/skills/blob/main/skills/.system/skill-installer/SKILL.md)
- [OpenAI — Skill Installer: implementação](https://github.com/openai/skills/blob/main/skills/.system/skill-installer/scripts/install-skill-from-github.py)
- [OpenAI Help Center — Skills no ChatGPT](https://help.openai.com/pt-br/articles/20001066-skills-in-chatgpt)
- [Agent Skills — especificação](https://agentskills.io/specification)

_Este guia descreve recursos documentados e observados; a instalação não foi executada remotamente no dispositivo do usuário._
