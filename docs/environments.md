# Ambientes, versionamento e metadados de build

Documento de referência para o ORBIT (**axonia.orbit.v1**), Fase 0 — sem configuração de infraestrutura nem runtime.

---

## Ambientes

### localhost

| | |
|---|---|
| **Finalidade** | Desenvolvimento e depuração na máquina do programador. |
| **Uso** | Correr a app localmente; testes rápidos; iterar sem impacto em utilizadores. |
| **Nível de risco** | Baixo para utilizadores finais; médio se forem ligados por engano a dados ou APIs sensíveis. |
| **Local ou cloud** | **Local.** |
| **Dados reais** | **Não** deve apontar para dados de produção. Usar dados locais, de desenvolvimento ou anonimizados. |

### preview

| | |
|---|---|
| **Finalidade** | Validar alterações (por exemplo ramo ou PR) antes de integração ou promoção a staging. |
| **Uso** | Partilhar com equipa ou stakeholders o comportamento de uma versão específica do código. |
| **Nível de risco** | Médio — erros visíveis a um grupo limitado, sem ser o tráfego de produção. |
| **Local ou cloud** | **Cloud** (deploy descartável ou de curta duração). |
| **Dados reais** | **Não** deve usar dados de produção. Dados de teste, sintéticos ou cópias controladas. |

### staging

| | |
|---|---|
| **Finalidade** | Ambiente pré-produção para testes finais, integração e validação operacional. |
| **Uso** | QA, regressão e ensaios de deploy antes de produção; comportamento o mais próximo possível de produção. |
| **Nível de risco** | Médio-alto — falhas podem afetar processos ou dados não produtivos críticos para testes. |
| **Local ou cloud** | **Cloud.** |
| **Dados reais** | **Não** substitui produção. Pode usar dados parecidos com produção apenas se forem **réplicas controladas** e políticas de privacidade o permitirem — nunca a base de produção como fonte de verdade para staging. |

### production

| | |
|---|---|
| **Finalidade** | Serviço em uso por utilizadores e operações reais. |
| **Uso** | Tráfego real, SLAs e decisões de negócio. |
| **Nível de risco** | **Alto** — impacto direto em utilizadores e dados. |
| **Local ou cloud** | **Cloud.** |
| **Dados reais** | **Sim** — dados reais de clientes e operação, sujeitos a políticas de segurança e compliance. |

---

## Política de versionamento e metadados de build

- **`VERSION` (raiz do repositório)** é a **única fonte de verdade** para a **versão oficial** do sistema (alinhada com SemVer e o `CHANGELOG.md`).
- Em fases posteriores, o sistema deve **expor automaticamente** (API ou payload de build, a definir na implementação):
  - **version** — lida a partir de `VERSION` (ou do artefacto de build derivado dele);
  - **environment** — um dos valores canónicos: `localhost`, `preview`, `staging`, `production`;
  - **git branch** e **git commit** — injetados no processo de build (não editados à mão em ficheiros de log);
  - **build date/time** — momento da geração do artefacto.
- **preview**, **staging** e **production** devem permitir identificar **claramente** qual o ambiente ativo (metadados + convenções de UI descritas abaixo).
- **localhost** deve identificar-se explicitamente como **localhost**, para nunca ser confundido com cloud.

---

## Regras para evitar erro humano

- **Não** depender de edição manual de ficheiros tipo `info.log` (ou equivalentes) para saber o ambiente — a identificação deve vir de **build/runtime** automatizado.
- A **UI** deve mostrar **ambiente** e **versão** numa **zona técnica e discreta** (por exemplo rodapé ou painel de contexto), visível para quem opera o sistema.
- Deve existir, mais à frente, uma **página técnica** dedicada, por exemplo **`/system/version`**, com versão, ambiente e metadados de build acordados.
- **Produção** e **staging** **não** podem ser **confundidos visualmente**: diferenciação consistente (etiqueta, cor ou padrão de UI) acordada na implementação.

---

## Leituras relacionadas

- `docs/architecture.md` — visão geral e encaixe operacional.
- `docs/decision-log.md` — decisões registadas sobre ambientes e versionamento.
