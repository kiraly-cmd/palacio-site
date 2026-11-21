# Palácios da Memória — Site público

Portal para estudo de sentenças judiciais em fluxogramas.

- `index.html`: página inicial com dois boxes: Palácio Cível e Palácio Criminal.
- `civel/index.html`: fluxograma vertical do Palácio Cível, com spin-offs e referências jurídicas.
- `criminal/index.html`: página de espera; módulo criminal ainda não desenvolvido.
- `normas/index.html`: consulta provisória com os Blocos A (Códigos do Sprint TJRS), B (legislação especial do Sprint TJRS) e C (demais metas prioritárias TJSC), expansível e pesquisável.
- `normas/dados.json`: cópia pública e resumida dos dados da Base Mestre após o último fechamento oficial.
- `normas/sprint-tjrs.json`: seleção explícita de metas para o Sprint TJRS (Blocos A e B); as não selecionadas ficam automaticamente no C.

**Este repositório é público** e contém apenas arquivos para apresentação. Não contém credenciais nem acesso ao repositório privado de conteúdo. Visitantes podem ler o HTML/JS publicado, mas não alterar o repositório sem permissão.

A publicação via GitHub Pages precisa ser habilitada em **Settings → Pages → Deploy from a branch → main → /(root)**.

A fonte oficial de edições e histórico é mantida separadamente. A sincronização do conteúdo privado com este repositório ainda **não está automatizada**.

## Atualização da aba provisória Legislação pendente

### Divisão em blocos para o Sprint TJRS (21/11/2026)

- **Bloco A — Códigos:** 14 metas selecionadas: Constituição Federal 1–6, CPC 1–4, Código Penal 1–2 e CPP 1–2.
- **Bloco B — Legislação especial:** 29 metas selecionadas: Lei 11.101/2005 (7), Lei 8.429/1992 (2), CTN (8), Lei 14.344/2022 (1), Lei 4.591/1964 (3), Lei 9.514/1997 (2), Lei 9.492/1997 (1), Lei 5.474/1968 (1), Lei 7.357/1985 (1), Lei 12.965/2014 (1), Lei 9.307/1996 (1) e Resolução CONAMA 237/1997 (1).
- **Bloco C — Demais pendentes:** é calculado a partir de todas as metas prioritárias ainda pendentes em `normas/dados.json` **menos cada meta individual incluída nos Blocos A ou B**. Uma norma parcialmente incluída no Sprint pode ter outras metas ainda no C; não duplicar nem omitir metas.
- **43 metas selecionadas e 25 vagas não preenchidas** dentro da capacidade de referência de 68 metas (17 dias x 4). O usuário optou por deixar as vagas em aberto, **sem complementação automática**.
- As seleções em `normas/sprint-tjrs.json` são independentes da execução; as contagens A/B/C exibidas representam **somente o saldo pendente no último fechamento**. A Meta 23 do Código Civil foi informada durante o dia aberto de 21/11, mas não deve ser abatida no site antes do fechamento.
- Para mudar seleção de Sprint, editar `normas/sprint-tjrs.json` com decisão expressa do usuário e verificar que os nomes de norma e identificadores de meta correspondem exatamente aos registros em `normas/dados.json`. A seleção não altera metas diárias, prioridades permanentes da Base Mestre nem histórico fechado. Após fechamentos regulares, atualizar `normas/dados.json` sem reescrever a seleção em `sprint-tjrs.json`.
- Auditar a igualdade `pendentes A + pendentes B + pendentes C = metas_prioritarias_pendentes`. O painel recusa exibição em caso de inconsistência e não acessa o repositório privado.


- A **fonte oficial de saldos** é o arquivo privado `kiraly-cmd/magistratura-central/base-mestre/legislacao-tjsc-indice-tematico-pendentes.json`.
- A página pública lê exclusivamente `normas/dados.json`; **não acessa** o repositório privado via navegador nem expõe credenciais.
- **Em cada fechamento diário confirmado**, primeiro atualizar/validar o índice oficial e **depois** substituir o conteúdo de `normas/dados.json` por um retrato resumido da mesma data. A página se atualiza sem alterar HTML.
- O JSON público guarda `tipo`, `data_base`, `atualizado_apos_fechamento`, `fonte`, `metas_prioritarias_pendentes`, `normas_pendentes`, `metas_extras_fora_indice` e `grupos`, cada grupo com `nome`, `quantidade_metas` e `normas`; cada norma com `nome`, `quantidade_metas` e `metas_pendentes`.
- Validar os totais: soma de metas das normas = `metas_prioritarias_pendentes`; soma de normas = `normas_pendentes`; não incluir metas extras nas metas prioritárias. Não incorporar produção de dia aberto.
- **A sincronização é feita no fluxo de fechamento do cronograma**; não existe automação GitHub Actions configurada para copiar dados privados. Se um fechamento não atualizar este repositório, a página mostrará a data do último retrato sincronizado.
- Quando `metas_prioritarias_pendentes` chegar a zero e houver confirmação do encerramento, retirar o atalho `href="normas/"` da página inicial e opcionalmente arquivar `normas/` para preservar o histórico. Não desativar antecipadamente.

**Privacidade:** o site e o JSON são públicos. Publicar apenas nomes de normas, metas restantes, disciplinas e data de atualização; não copiar informações pessoais, arquivos privados, registros diários completos ou tokens.
