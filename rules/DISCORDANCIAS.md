# Discordâncias entre fontes

Registro obrigatório (ver `CLAUDE.md`/brief do projeto): toda discordância entre fontes
precisa estar documentada aqui, com qual lado foi adotado e por quê — nunca escondida
num commit ou resolvida em silêncio.

## 1. Infarto / AVC / convulsão / dor torácica intensa: UPA ou 192?

- **Fonte SP** (`sp-quando-upa`): lista "infarto", "AVC", "convulsões" e "dor no peito
  intensa" como situações que a UPA atende — explica que UPA é pra urgência "que não
  configura emergência com risco iminente de vida", e que UPAs em geral têm estrutura
  pra estabilização inicial (ECG, desfibrilador) antes de transferir pro hospital.
- **Fonte Einstein** (`einstein-quando-ps`): a mesma lista de sintomas (dor no peito
  intensa, perda súbita de força/fala, convulsão) está na lista de "quando ir ao
  pronto-socorro", tratada como emergência direta.

**Adotado nesse rascunho:** mantive esses sintomas em `sinais_alerta.yaml` apontando
pra `urgencia_192` (ligar o SAMU), não UPA — é a leitura mais conservadora das duas,
e o brief é explícito: "na dúvida, a resposta é a mais conservadora". Uma pessoa leiga
preenchendo um formulário não tem como saber se a UPA mais próxima tem capacidade de
estabilizar um infarto; errar pro lado do SAMU é mais seguro que errar pro lado da UPA.

**Isso precisa de validação de um profissional de saúde antes de ir pra qualquer uso
além de demo** — pode ser que a leitura correta seja UPA mesmo, dependendo da estrutura
real das UPAs de Niterói, que eu não tenho como avaliar.

## 2. Febre: UBS ou UPA?

- **Fonte Caderno 28/MS** (`cab28-v2`, p.20): "febre sem complicação" é exemplo de
  "atendimento prioritário" dentro do próprio fluxo de acolhimento da UBS — sugere que
  UBS é o lugar certo.
- **Fonte SP** (`sp-quando-upa`): febre acima de 39°C é critério explícito pra UPA.

**Adotado:** não é uma discordância real, é complementar — tratei como limiar: febre
sem outras complicações e **abaixo** de 39°C fica com a UBS (regra `febre_sem_complicacao`
em `330330.yaml`); febre **acima** de 39°C vai pra UPA (regra `febre_acima_39`). Ambas
`pendente_revisao`.
