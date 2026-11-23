# Prompt Elaboration

**Agent Skill para transformar objetivos, bugs, otimizações e pedidos informais em um prompt claro, proporcional e pronto para copiar.**

A skill **não executa a tarefa**: ela prepara a solicitação para outro agente, identifica perguntas realmente necessárias e recomenda, quando relevante, o modelo, o nível de raciocínio, o modo Planejamento e outras skills adequadas.

**Versão:** `1.1` · **Idioma:** Português (Brasil)

## O que faz

- Reescreve pedidos imprecisos sem inventar causas, métricas, arquivos ou requisitos.
- Preserva a intenção: investigar, corrigir, implementar, otimizar, revisar ou planejar.
- Pergunta apenas quando uma decisão do usuário altera materialmente a missão.
- Gera **um único prompt copiável**, sem etapas ou listas excessivas.
- Sugere configurações conforme o **agente de destino**, não conforme a interface que está gerando o prompt.
- Recomenda outras skills **opcionais**, como Ponytail, Caveman e `rbx-*`, sem invocá-las automaticamente.
- Prioriza economia de desperdício, não redução da qualidade técnica.

## Releases e download

- **[Última release](https://github.com/gubertaglia/prompt-elaboration/releases/latest)** — versão estável e notas de atualização.
- **[Baixar a v1.1 para o Codex (.zip)](https://github.com/gubertaglia/prompt-elaboration/releases/download/v1.1/prompt-elaboration-v1.1.zip)** — contém a pasta `prompt-elaboration/` pronta para instalar.

**Observação:** o botão **Code → Download ZIP** baixa o código-fonte completo; para instalar a skill, prefira o arquivo anexado à release.

## Instalar no Codex

Instale a pasta completa deste repositório com o nome `prompt-elaboration` dentro do **diretório de skills reconhecido pelo seu Codex**. A estrutura final deve ser:

```text
<skills>/
└── prompt-elaboration/
    ├── SKILL.md
    └── agents/
        └── openai.yaml
```

**Windows:** use o diretório de skills que sua instalação já reconhece (por exemplo, `%USERPROFILE%\.agents\skills` ou, em instalações que usam essa localização, `%USERPROFILE%\.codex\skills`). Evite instalar cópias duplicadas em ambos os locais.

No seletor de skills, invoque:

```text
$prompt-elaboration corrija as quedas de FPS quando há muitas explosões no meu sistema voxel Roblox
```

> **Nota:** `\$prompt-elaboration` é a forma de seleção de skill prevista para o Codex com esse seletor. Escrever `/prompt-elaboration` não é necessariamente equivalente.

## Usar no ChatGPT Web

Se sua conta tiver suporte nativo à instalação de skills, a disponibilidade e o procedimento dependem do produto e da configuração da conta. **Não presuma que instalar no Codex a disponibiliza automaticamente no ChatGPT Web.**

Como alternativa, crie um **Projeto** no ChatGPT e copie as instruções de [CHATGPT_WEB.md](CHATGPT_WEB.md). Essa opção reproduz o comportamento, mas não equivale à instalação de uma Agent Skill nativa.

## Exemplo de saída

**Entrada:** `Corrija as quedas de FPS quando muitas explosões acontecem no meu sistema voxel.`

**Configuração sugerida:** depende do modelo/controles disponíveis no agente que executará o prompt.

**Skill sugerida:** `$rbx-optimize`, quando instalada e o projeto for Roblox.

**Prompt para copiar:**

> Investigue e corrija as quedas de FPS quando muitas explosões acontecem no meu sistema voxel. Identifique os gargalos responsáveis e implemente as otimizações adequadas, preservando a jogabilidade e os efeitos relevantes. Verifique de forma proporcional se o cenário afetado melhorou e se houve regressões importantes.

## Arquivos

- [`SKILL.md`](SKILL.md): comportamento, limitações, perguntas e formato de resposta.
- [`agents/openai.yaml`](agents/openai.yaml): metadados de interface e política de invocação.
- [`CHATGPT_WEB.md`](CHATGPT_WEB.md): instruções alternativas para um Projeto no ChatGPT Web.
- [`CHANGELOG.md`](CHANGELOG.md): histórico de versões.

## Compatibilidade e limites

Esta versão foi preparada para o formato de Agent Skills utilizado pelo Codex, mas **a descoberta, os metadados aceitos e a disponibilidade no ChatGPT Web dependem da superfície do produto**. Não há garantia de disponibilidade de modelos específicos ou de controles idênticos entre plataformas.

**Validação:** pacote e estrutura conferidos. Não há resultados de testes comportamentais reais com o Codex ou o ChatGPT Web publicados neste repositório.

## Fontes de referência

- [OpenAI — documentação do Codex](https://developers.openai.com/codex/skills)
- [Agent Skills — especificação](https://agentskills.io/specification)

Este repositório não inclui licença de código aberta definida. A escolha de uma licença pode ser feita separadamente pelo mantenedor.
## Manutenção das releases

O workflow [Publish skill release](.github/workflows/release.yml) monta e valida o ZIP instalável. Para uma versão futura, atualize `SKILL.md`, `CHANGELOG.md` e o número de versão exibido neste README; depois execute **Actions → Publish skill release → Run workflow** e informe a tag da nova versão (por exemplo, `v1.2`).

**GitHub Packages não é necessário**: a distribuição é feita por arquivos ZIP anexados às GitHub Releases.
