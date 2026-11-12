# Palácios da Memória — Site público

Portal para estudo de sentenças judiciais em fluxogramas.

- `index.html`: página inicial com dois boxes: Palácio Cível e Palácio Criminal.
- `civel/index.html`: fluxograma vertical do Palácio Cível, com spin-offs e referências jurídicas.
- `criminal/index.html`: página de espera; módulo criminal ainda não desenvolvido.
- `normas/index.html`: consulta provisória, expansível e pesquisável de normas prioritárias pendentes por disciplina.
- `normas/dados.json`: cópia pública e resumida dos dados da Base Mestre após o último fechamento oficial.

**Este repositório é público** e contém apenas arquivos para apresentação. Não contém credenciais nem acesso ao repositório privado de conteúdo. Visitantes podem ler o HTML/JS publicado, mas não alterar o repositório sem permissão.

A publicação via GitHub Pages precisa ser habilitada em **Settings → Pages → Deploy from a branch → main → /(root)**.

A fonte oficial de edições e histórico é mantida separadamente. A sincronização do conteúdo privado com este repositório ainda **não está automatizada**.

## Atualização da aba provisória Legislação pendente

- A **fonte oficial de saldos** é o arquivo privado `kiraly-cmd/magistratura-central/base-mestre/legislacao-tjsc-indice-tematico-pendentes.json`.
- A página pública lê exclusivamente `normas/dados.json`; **não acessa** o repositório privado via navegador nem expõe credenciais.
- **Em cada fechamento diário confirmado**, primeiro atualizar/validar o índice oficial e **depois** substituir o conteúdo de `normas/dados.json` por um retrato resumido da mesma data. A página se atualiza sem alterar HTML.
- O JSON público guarda `tipo`, `data_base`, `atualizado_apos_fechamento`, `fonte`, `metas_prioritarias_pendentes`, `normas_pendentes`, `metas_extras_fora_indice` e `grupos`, cada grupo com `nome`, `quantidade_metas` e `normas`; cada norma com `nome`, `quantidade_metas` e `metas_pendentes`.
- Validar os totais: soma de metas das normas = `metas_prioritarias_pendentes`; soma de normas = `normas_pendentes`; não incluir metas extras nas metas prioritárias. Não incorporar produção de dia aberto.
- **A sincronização é feita no fluxo de fechamento do cronograma**; não existe automação GitHub Actions configurada para copiar dados privados. Se um fechamento não atualizar este repositório, a página mostrará a data do último retrato sincronizado.
- Quando `metas_prioritarias_pendentes` chegar a zero e houver confirmação do encerramento, retirar o atalho `href="normas/"` da página inicial e opcionalmente arquivar `normas/` para preservar o histórico. Não desativar antecipadamente.

**Privacidade:** o site e o JSON são públicos. Publicar apenas nomes de normas, metas restantes, disciplinas e data de atualização; não copiar informações pessoais, arquivos privados, registros diários completos ou tokens.
