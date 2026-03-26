# Arquitetura

Na Fase 0 não existe arquitetura de runtime implementada neste repositório.

O alvo de stack (Next.js com TypeScript em modo strict, Supabase, Vercel) e as restrições de segurança multi-tenant estão definidos em `.cursorrules` e serão detalhados aqui à medida que o desenho evoluir.

A arquitetura **operacional** prevê **separação explícita por ambientes** (localhost, preview, staging, production), descrita em `docs/environments.md`. A **identificação de versão, de build e de ambiente** integra a **base** do sistema (metadados automáticos em fases posteriores), sem duplicar aqui decisões ainda não fixadas na implementação.
