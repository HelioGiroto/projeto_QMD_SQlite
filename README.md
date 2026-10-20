# projeto_QMD_SQlite

Objetivo

Experimento que combina QMD para recuperar evidências textuais com SQLite para armazenar entidades, relações e metadados das transcrições.

O que faz

- Indexa as transcrições no QMD.
- Armazena entidades como conceitos, pessoas, obras e temas.
- Armazena relações entre entidades.
- Liga cada relação ao trecho original por meio de source_chunk_id.
- Como as transcrições não possuem timestamp, usa arquivo, ID do vídeo, linhas, hash do chunk ou citação literal como referência.
- Usa SQLite para consultas estruturadas e QMD para recuperar o texto exato.
- Testa uma arquitetura simples, persistente e fácil de fazer backup.

Tecnologias previstas

- QMD: busca lexical, semântica e reranking.
- SQLite: banco local para entidades, relações, chunks e metadados.
- Python: ingestão, consultas e integração.
- Hermes Agent: perguntas, orquestração e geração da resposta.
- MCP: exposição das ferramentas de busca ao Hermes.
- Markdown: transcrições originais.

Fonte de dados

As transcrições Markdown sem timestamp são a fonte oficial de informações de todos os projetos e ficam em:

/home/clone/transcricoes_md

As respostas devem citar o arquivo Markdown e o título/ID do vídeo. O sistema não deve inventar timestamps.

Modelo inicial

- entities: id, nome e tipo.
- relations: origem, destino, tipo da relação, confiança e source_chunk_id.
- chunks: vídeo, timestamps, texto e hash.

Fluxo previsto

transcrições -> QMD e SQLite -> Hermes -> relações confirmadas por trechos originais

Vantagem experimental

Esta combinação separa busca textual de raciocínio estruturado sem exigir um banco de grafos dedicado. O SQLite deve ser a fonte das relações e o QMD deve ser a fonte da evidência textual.

Status

Experimento recomendado para comparar simplicidade, persistência e rastreabilidade.

Gateway

O nome a ser chamado no gateway, inclusive no WhatsApp, será Sand. Sand responderá em primeira pessoa como autor virtual baseado nas transcrições, sem afirmar ser a pessoa real.

## Licença

Este projeto está licenciado sob a Licença MIT.

Autor: Hélio Giroto
Data: 2026-10-19
