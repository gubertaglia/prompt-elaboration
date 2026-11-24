# Changelog

## v1.3 — 2026-11-23

- Definidos critérios de aceitação proporcionais e reutilização de achados e baselines válidos.
- Adicionado controle de execução seletivo para tarefas complexas: consultas sob demanda, agrupamento seguro de operações e retornos focados em evidência acionável.
- Melhorada a coordenação entre skills complementares, evitando fluxos de trabalho, investigações e validações duplicados.
- Reforçados os critérios de encerramento e a reavaliação de investigações estagnadas, sem aprovações intermediárias obrigatórias.
- Tratamento de orçamento informado pelo usuário quando observável, sem presumir acesso à cota ou prometer economia.
- Recomendações de modelo, raciocínio e skills ajustadas ao custo e à complexidade da missão, sem reduzir a qualidade necessária.
- Preservados o caráter universal, a geração de um único prompt, a invocação explícita e a compatibilidade estrutural CHAT/CODEX. Alinhamento com Roblox Engineering Skills v2.0.0 quando pertinente.
- Validação estrutural do pacote; testes comportamentais e economia quantitativa de cota ainda não comprovados.

## v1.2 — 2026-11-23

- Aperfeiçoada a elaboração de prompts com verificações proporcionais ao impacto, risco e incerteza.
- Incentivado o reaproveitamento de código, logs e evidências existentes antes de impor novos testes ou pesquisas.
- Evitadas exigências genéricas de benchmarks, ciclos repetidos de ferramentas, validações ou investigações sem critério de parada.
- Mantidos testes necessários ou solicitados, com distinção entre hipótese, inferência e medição.
- Modo Planejamento não deve ser recomendado apenas para criar uma etapa adicional de validação.
- Skill continua generalista, produzindo apenas prompts; skills Roblox, Ponytail e Caveman permanecem sugestões opcionais.


## Atualização de documentação após v1.1 — 2026-11-23

- Explicada a instalação nativa no ChatGPT Web por **Adicionar → Carregar do seu computador**, quando disponível.
- Verificado no Skill Installer oficial o uso de `--path . --name prompt-elaboration` para uma skill com `SKILL.md` na raiz do repositório.
- Criado guia `INSTALL.md` com download do ZIP, instalação manual no Windows, verificação, atualizações e solução de problemas.
- Mantido o artefato da release `v1.1` sem alteração; esta atualização modifica apenas a documentação da branch `main`.

## v1.1 — 2026-11-23

- Refinada a fronteira entre gerar um prompt e executar a missão.
- Reforçada a proteção contra instruções contidas em dados, arquivos e logs consultados.
- Configurações sugeridas passaram a considerar a superfície **de destino** do prompt.
- Melhorados os critérios para perguntas essenciais e verificações proporcionais.
- Recomendações de Ponytail, Caveman e skills Roblox permanecem opcionais e manuais.
- Documentado o uso alternativo no ChatGPT Web por instruções de Projeto.

## v1.0 — 2026-11-23

- Primeira versão da skill `prompt-elaboration`.