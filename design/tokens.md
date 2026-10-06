# Design tokens — MEDME

Decisão (2026-10-03): o frontend segue o **Padrão Digital de Governo (gov.br Design System)** 100%, não um design próprio — https://www.gov.br/ds/home. Faz sentido pro produto: é orientação de saúde pública, parecer um serviço oficial do governo é propriedade, não imitação.

Fonte: `@govbr-ds/core` v3.7.0 (CSS compilado, extraído direto — não suposição visual), mantido pelo SERPRO. Componentes React oficiais em `@govbr-ds/react-components` (mesma organização mantenedora).

## Cor

| Token oficial | Hex | Uso no MEDME |
|---|---|---|
| `--color-primary-default` | `#1351b4` | Ação normal, navegação, **UBS** |
| `--color-primary-darken-01/02` | `#0c326f` / `#071d41` | Hover/texto sobre fundo claro |
| `--color-primary-lighten-01/02` | `#2670e8` / `#5992ed` | Estados hover/focus |
| `--color-primary-pastel-01/02` | `#c5d4eb` / `#dbe8fb` | Fundos suaves, badges |
| `--warning` (`yellow-vivid-20`) | `#ffcd07` | **UPA** (nível intermediário) |
| `--danger` (`red-vivid-50`) | `#e52207` | **Sinal de alerta / urgência / 192** — é literalmente a cor de perigo oficial, não precisei inventar nada aqui |
| `--success` (`green-cool-vivid-50`) | `#168821` | Confirmações |
| `--info` (`blue-warm-vivid-60`) | `#155bcb` | Mensagens informativas |
| Neutros (`color-secondary-01..09`) | `#fff` → `#000` em 9 passos | Texto, fundo, bordas |

Mapeamento direto pro nosso domínio: **UBS = primary, UPA = warning, urgência/192 = danger**. O sistema de 3 níveis que já tínhamos desenhado já existe pronto no gov.br DS.

## Tipografia

Fonte oficial: **Rawline** (fallback Raleway, sans-serif) — `--font-family-base: Rawline, Raleway, sans-serif`.

## Componentes

Usar os componentes do `@govbr-ds/react-components` diretamente, não recriar na mão. Classes CSS subjacentes (se precisar de algo fora do pacote React) seguem prefixo `.br-*`: `br-button`, `br-input`, `br-card`, `br-message`, `br-switch`, `br-modal`, etc. — lista completa em `/ds/components/*`.

## Layout

Sistema de grid próprio do gov.br DS (`/ds/fundamentos-visuais/grid`) e espaçamento em escala (`--spacing-scale-*x`, múltiplos de 4px). Seguir a densidade e os templates oficiais (`/ds/templates/base`) em vez de layout customizado.

## Restrições

- Não inventar cor fora da paleta oficial.
- Não inventar componente visual que já existe no DS (botão, input, card, mensagem de alerta — tudo já vem pronto).
- Gradientes/decoração fora do sistema: evitar, não é o padrão do gov.br DS.
