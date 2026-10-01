# T-Line — Formulário mocado (Web-to-Lead)

Site estático usado na homologação da T-Line para testar a criação de Lead "puro" (via Web-to-Lead), sem passar pelo wizard interno que converte o Lead em Oportunidade na mesma transação.

- `index.html` — réplica visual da página de oferta (Compass) com o formulário "Estou Interessado", postando via Web-to-Lead para o Salesforce T-Line Homolog (org `00D8900000622og`).
- `obrigado.html` — página de retorno (`retURL`) exibida após o envio.

A barra amarela no topo permite escolher a concessionária e o segmento de destino de cada envio de teste.

## Mapeamento de campos

| Formulário | Campo Lead | Nome no POST |
|---|---|---|
| Nome (dividido em nome/sobrenome) | FirstName / LastName | `first_name` / `last_name` |
| E-mail | Email | `email` |
| Telefone | Phone | `phone` |
| CPF | CA_CPF__c | `00N89000005pAFJ` |
| Contato por E-mail / Whatsapp / Telefone | CA_AceiteEmail__c / CA_AceiteWhatsApp__c / CA_AceiteTelefone__c | `00N89000005pAFE` / `00N89000005pAFH` / `00N89000005pAFG` |
| (oculto) Origem | LeadSource = `Site` | `lead_source` |
| (oculto) Concessionária | CA_Concessionaria__c | `00N89000005pAFL` |
| (oculto) Segmento | CA_SegmentoAtendimento__c | `00N890000060Kkr` |
| (oculto) Grupo de produto | CA_GrupoProduto__c | `00N89000005pJdd` |
| (oculto) Marca / Modelo | CA_Marca__c / CA_Modelo__c | `00N89000006Xdom` / `00N89000006Xdon` |
| (oculto) Sub-origem | CA_SubOrigem__c = `Homologação - Formulário Site` | `00N89000005pJdg` |

Os Ids `00N...` dos campos customizados são da org Homolog — mudam em outra org.

Hospedado via GitHub Pages a partir da branch `main`.
