# Prompt Elaboration

**Agent Skill para transformar objetivos, bugs, otimizações e pedidos informais em um prompt claro, proporcional e pronto para copiar.**

A skill **não executa a tarefa**: ela prepara a solicitação para outro agente, identifica perguntas realmente necessárias e recomenda, quando relevante, o modelo, o nível de raciocínio, o modo Planejamento e outras skills adequadas.

**Versão:** `1.4` · **Idioma:** Português (Brasil)

## O que faz

- Reescreve pedidos imprecisos sem inventar causas, métricas, arquivos ou requisitos.
- Preserva a intenção: investigar, corrigir, implementar, otimizar, revisar ou planejar.
- Pergunta apenas quando uma decisão do usuário altera materialmente a missão.
- Gera **um único prompt copiável**, sem etapas ou listas excessivas.
- Sugere configurações conforme o **agente de destino**, não conforme a interface que está gerando o prompt.
- Recomenda outras skills **opcionais**, como Ponytail, Caveman e `rbx-*`, sem invocá-las automaticamente.
- Prioriza economia de desperdício, não redução da qualidade técnica.
- Preserva a responsabilidade pela validação: manual, híbrida ou autônoma, conforme a preferência e autorização do usuário.
- Define critérios de aceitação como resultados, sem antecipar cenários, benchmarks ou procedimentos desnecessários; favorece implementação fundamentada e checagens estáticas pertinentes.
- Delega métodos às skills especializadas, inclusive Roblox Engineering Skills v2.1.0 quando pertinente, sem tornar a skill dependente do Roblox.
- Adiciona controle de execução somente quando material: escopo, evidências reutilizáveis, operações focadas, coordenação entre skills e critérios de conclusão.
- Considera orçamento explicitamente informado sem presumir telemetria ou impor limites arbitrários; não promete redução de cota.

## Por que a v1.4 existe

Durante o desenvolvimento de um sistema voxel, o mantenedor observou uma execução do Codex Plus que durou cerca de 24 minutos e consumiu 95 pontos percentuais da janela de cinco horas. Foram registradas 108 chamadas de ferramentas e aproximadamente 14,7 milhões de tokens acumulados, incluindo cache. Em tarefas posteriores, o mantenedor identificou operações de Play/Stop, medições e verificações como atividades que prefere realizar pessoalmente.

A v1.3 já buscava reduzir trabalho redundante, mas ainda podia incentivar prompts com cenários de teste, métricas e confirmações antecipadas antes de o executor conhecer a alteração. A v1.4 distingue o **resultado pretendido** do **método de validação** e preserva quem é responsável pelos testes. Isso evita transformar verificações opcionais em requisitos e favorece a implementação quando a evidência é suficiente.

As observações não constituem um experimento controlado: não demonstram que testes, modelo ou skills isoladamente causaram o consumo. A skill não monitora a cota, não promete economia e não deve omitir evidências essenciais de segurança, correção ou integridade.

### Responsabilidade pela validação

| Preferência do usuário | Comportamento do prompt |
| --- | --- |
| Manual | Deixar testes práticos e medições com o usuário; preservar análise, implementação autorizada e checagens estáticas pertinentes. |
| Híbrida | Autorizar somente os testes práticos especificados; delegar os demais. |
| Autônoma | Preservar os testes e medições solicitados; deixar a estratégia proporcional a cargo do executor. |
| Não especificada | Não inventar preferência nem autorização ampla; delegar métodos ao projeto, às skills e às permissões existentes. |

Essas modalidades são critérios de elaboração, não configurações nativas do Codex. Se a validação prática for indispensável para avançar com segurança, o executor deve explicar a lacuna e respeitar a autorização; ganhos não medidos não são ganhos comprovados.

## Instalação rápida

Escolha a interface onde pretende utilizar a skill. **Instalar no Codex não a instala automaticamente no ChatGPT Web, nem vice-versa.** Consulte o [guia completo](INSTALL.md).

| Plataforma | Método recomendado |
| --- | --- |
| **ChatGPT Web** | Abra [Habilidades](https://chatgpt.com/skills) → **Adicionar** → **Carregar do seu computador** → selecione o ZIP da release. A opção depende da sua conta e pode exigir análise do arquivo. |
| **Codex Desktop** | Use a skill integrada `$skill-installer` com o repositório, `--path .`, `--name prompt-elaboration` e a ref `v1.4`; ou instale manualmente o ZIP. |

### Downloads

- **[Release estável v1.4](https://github.com/gubertaglia/prompt-elaboration/releases/tag/v1.4)**
- **[Baixar skill v1.4 (.zip)](https://github.com/gubertaglia/prompt-elaboration/releases/download/v1.4/prompt-elaboration-v1.4.zip)** — ZIP instalável, contendo somente a pasta `prompt-elaboration/`.
- [Todas as releases](https://github.com/gubertaglia/prompt-elaboration/releases).

Use o **ZIP anexado à release**, não o botão **Code → Download ZIP** do GitHub, quando a intenção for instalar a skill manualmente.

### Exemplo: Skill Installer no Codex

No chat do Codex Desktop, selecione `$skill-installer` e envie:

```text
Instale a skill do repositório gubertaglia/prompt-elaboration,
usando --ref v1.4 --path . --name prompt-elaboration.
Instale no diretório de skills reconhecido por este Codex,
sem modificar as outras skills.
```

O código atual do instalador oficial admite o caminho `.` com nome explícito; isso **não equivale a um teste real no seu computador**. Como `SKILL.md` está na raiz, não é necessário criar `skills/prompt-elaboration/` no repositório só para essa instalação. O método pela raiz pode copiar arquivos documentais adicionais; prefira o ZIP da release para uma instalação mínima.

Após instalar no Codex, procure:

```text
$prompt-elaboration corrija as quedas de FPS quando há muitas explosões no meu sistema voxel Roblox
```

Em uma instalação manual típica do Windows, a pasta ficará em `%USERPROFILE%\.codex\skills\prompt-elaboration\`; use o local realmente reconhecido pelo seu Codex (que pode ser diferente). O seletor `$` é do Codex; não presuma a mesma sintaxe no ChatGPT Web.

## Exemplo de saída

**Entrada:** `Corrija as quedas de FPS quando muitas explosões acontecem no meu sistema voxel.`

**Configuração sugerida:** depende do modelo/controles disponíveis no agente que executará o prompt.

**Skill sugerida:** `$rbx-optimize`, quando instalada e o projeto for Roblox.

**Prompt para copiar:**

> Investigue e corrija as quedas de FPS quando muitas explosões acontecem no meu sistema voxel. Identifique os gargalos responsáveis e implemente as otimizações adequadas, preservando a jogabilidade e os efeitos relevantes.

**Se o usuário informou que fará os testes:** acrescentar ao prompt apenas a restrição relevante, por exemplo: "Priorize a análise e a implementação no código. Eu realizarei os testes práticos e as medições no Roblox Studio." Não prescrever ciclos de Play/Stop ou uma matriz de testes por padrão.

## Arquivos

- [`SKILL.md`](SKILL.md): comportamento, limitações, perguntas e formato de resposta.
- [`agents/openai.yaml`](agents/openai.yaml): metadados de interface e política de invocação.
- [`INSTALL.md`](INSTALL.md): instalação pelo ChatGPT Web, Skill Installer do Codex e ZIP manual, com solução de problemas.
- [`CHATGPT_WEB.md`](CHATGPT_WEB.md): instalação nativa no ChatGPT Web e alternativa por instruções de Projeto.
- [`CHANGELOG.md`](CHANGELOG.md): histórico de versões.

## Compatibilidade e limites

Esta versão foi preparada para o formato de Agent Skills utilizado pelo Codex, mas **a descoberta, os metadados aceitos e a disponibilidade no ChatGPT Web dependem da superfície do produto**. Não há garantia de disponibilidade de modelos específicos ou de controles idênticos entre plataformas.

**Validação:** estrutura e conteúdo da skill conferidos localmente. O workflow de publicação gera e testa o ZIP instalável; testes comportamentais no dispositivo e economia de cota permanecem não comprovados.

## Fontes de referência

- [OpenAI — Skills no ChatGPT](https://help.openai.com/pt-br/articles/20001066-skills-in-chatgpt)
- [OpenAI — Skill Installer (código e instruções)](https://github.com/openai/skills/blob/main/skills/.system/skill-installer/SKILL.md)
- [OpenAI — documentação de skills](https://learn.chatgpt.com/docs/build-skills)
- [Agent Skills — especificação](https://agentskills.io/specification)

Este repositório não inclui licença de código aberta definida. A escolha de uma licença pode ser feita separadamente pelo mantenedor.

## Manutenção das releases

O workflow [Publish skill release](.github/workflows/release.yml) monta e valida o ZIP instalável. Para uma versão futura, atualize `SKILL.md`, `CHANGELOG.md` e o número de versão exibido neste README; depois execute **Actions → Publish skill release → Run workflow** e informe a tag da nova versão (por exemplo, `v1.4`).

**GitHub Packages não é necessário**: a distribuição é feita por arquivos ZIP anexados às GitHub Releases.
