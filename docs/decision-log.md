# Decision log

Registo cronológico de decisões relevantes para o ORBIT.

## 2026-03-26 — Fundação do repositório (Fase 0)

- Criação do projeto **ORBIT** (AXONIA).
- Repositório: **axonia.orbit.v1**.
- **Versão:** ficheiro `VERSION` na raiz do repositório como fonte única de verdade para a versão oficial do sistema.
- **Ambiente / build:** mais à frente, o sistema deve identificar automaticamente ambiente e build; a implementação fica para fases posteriores.

## 2026-03-26 — Estratégia de ambientes e metadados de build

- **Aprovação** da estratégia de versionamento **central** em `VERSION` na raiz (fonte única de verdade), em linha com o registo anterior e com `docs/environments.md`.
- **Distinção formal** dos ambientes **localhost**, **preview**, **staging** e **production** (finalidade, uso, risco, local vs cloud, dados reais) — ver `docs/environments.md`.
- **Decisão** de **automatizar** metadados de build (versão derivada de `VERSION`, ambiente, ramo e commit Git, data/hora de build) e a **identificação explícita do ambiente** em runtime — **implementação nas fases seguintes**, sem configuração de infra nesta tarefa.

## 2026-03-26 — Governação do repositório, roadmap e infra (documental)

- **Roadmap por fases** mantido no repositório (`docs/roadmap.md`), com **Fase 0** como fase atual e regra de **backlog** para ideias fora do scope corrente.
- **Infraestrutura mínima** descrita em documento próprio (`docs/infra.md`), alinhada a `docs/environments.md`, **sem** configuração técnica nem URLs finais nesta fase.
- **Segredos e variáveis de ambiente** permanecem **fora** do repositório; ficheiros `.env` ignorados pelo Git, com possibilidade de ficheiros de exemplo (`.env.example` / `.env.sample`) quando aplicável.
