# Infraestrutura — notas mínimas (Fase 0)

Documento **apenas descritivo**: sem configuração técnica neste repositório, sem URLs finais aprovadas e sem credenciais.

## O que já está decidido

| Ambiente | Alojamento (visão) |
|----------|-------------------|
| **localhost** | App e ferramentas de desenvolvimento na máquina local. |
| **preview** | Deploys de pré-visualização na **Vercel**. |
| **staging** | **Cloud**, separado de produção. |
| **production** | **Cloud**, dedicado a tráfego real. |

- **Supabase local:** **não** faz parte do scope desta fase; não usar Supabase local enquanto esta política vigorar.
- **Variáveis de ambiente e segredos:** **não** são commitados no repositório (ver `.gitignore`); exemplos podem existir como `.env.example` / `.env.sample` quando existir código que os justifique.
- **Staging** e **production** devem ter **configuração separada** (projeto, variáveis, bases de dados ou instâncias conforme definido mais à frente).

## Relação com outros documentos

- Ambientes (finalidade, risco, dados): `docs/environments.md`.
- Roadmap: `docs/roadmap.md`.

## O que ainda não está fixado aqui

- URLs, nomes de projetos na Vercel/Supabase, regiões e detalhes de rede — apenas após aprovação explícita e fora do scope desta tarefa.
