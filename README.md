# T-Line — Formulário mocado (Web-to-Lead)

Site estático usado na homologação da T-Line para testar a criação de Lead "puro" (via Web-to-Lead), sem passar pelo wizard interno que converte o Lead em Oportunidade na mesma transação.

- `index.html` — réplica visual da página de oferta (Compass) com o formulário "Estou Interessado", postando via Web-to-Lead para o Salesforce T-Line Homolog (org `00D8900000622og`).
- `obrigado.html` — página de retorno (`retURL`) exibida após o envio.

A barra amarela no topo permite escolher a concessionária, o segmento e a origem do Lead de cada envio de teste. GROW e NBS Gold são ignorados pelos flows de duplicidade (`CA_LeadIdentificacaoDuplicidade` e `CA_LeadValidarOportunidadeAbertaDuplicada`).

## Mapeamento de campos

| Formulário | Campo Lead | Nome no POST |
|---|---|---|
| Nome (dividido em nome/sobrenome) | FirstName / LastName | `first_name` / `last_name` |
| E-mail | Email | `email` |
| Telefone | Phone | `phone` |
| CPF | CA_CPF__c | `00N89000005pAFJ` |
| Contato por E-mail / Whatsapp / Telefone | CA_AceiteEmail__c / CA_AceiteWhatsApp__c / CA_AceiteTelefone__c | `00N89000005pAFE` / `00N89000005pAFH` / `00N89000005pAFG` |
| (barra de homologação) Origem do Lead — Site (padrão), MarketPlace, Meta, GROW, NBS Gold | LeadSource | `lead_source` |
| (oculto) Código da concessionária | CA_CodigoConcessionaria__c → o flow `CA_LeadAtribuirConcessionaria` preenche o lookup CA_Concessionaria__c | `00N89000005pAFK` |
| (oculto) Segmento | CA_SegmentoAtendimento__c | `00N890000060Kkr` |
| (oculto) Grupo de produto | CA_GrupoProduto__c | `00N89000005pJdd` |
| (oculto) Marca / Modelo | CA_Marca__c / CA_Modelo__c | `00N89000006Xdom` / `00N89000006Xdon` |
| (oculto) Sub-origem | CA_SubOrigem__c = `Homologação - Formulário Site` | `00N89000005pJdg` |

| (oculto) Blindagem / Financiamento / Veículo na Troca = `Não Ofertado` | CA_Blindagem__c / CA_Financiamento__c / CA_VeiculoNaTroca__c | `00N89000006RUWP` / `00N89000006RUWQ` / `00N89000006RUWR` |
| (oculto) Total de tentativas = `0` | CA_TotalTentativas__c | `00N89000005pJdi` |

Os Ids `00N...` dos campos customizados são da org Homolog — mudam em outra org.

O Web-to-Lead não aplica valores padrão de picklist/número para campos que não vêm no POST (os outros canais aplicam), por isso esses defaults vão explícitos como campos ocultos.

Web-to-Lead não aceita campos lookup, por isso a concessionária vai pelo código (`CA_CodigoIdentificador__c` da concessionária): 1 Jeep Ram SJC · 2 Jeep Ram Caraguatatuba · 3 Leapmotor SJC · 4 Seminovos SJC · 30 Toyota Washington Luiz · 31 T-Service João Dias.

Hospedado via GitHub Pages a partir da branch `main`.
