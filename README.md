# Angola Online Payment Gateway
[![License Code: MIT](https://img.shields.io/badge/code-MIT-green.svg)]()
[![License Content: CC BY 4.0](https://img.shields.io/badge/content-CC%20BY%204.0-blue.svg)]()

Repositório comunitário para **reunir informação prática** sobre gateways de pagamento, agregadores, bancos, *mobile money*, POS/TPA, e **pagamentos por referência** usados em Angola. Objetivo: facilitar a vida de quem quer **começar rápido**, com fontes, contactos, requisitos e dicas técnicas/legais.
> ⚠️ **Estado**: Este repositório **esta em desenvolvimento**.


> ⚠️ **Aviso legal**: Este projeto é colaborativo e **não** representa, nem é afiliado, patrocinado, endossado ou associado a quaisquer marcas, bancos, operadoras, gateways, agregadores ou entidades citadas.  
<br>Nomes e logótipos mencionados são propriedade dos seus titulares.
As informações aqui reunidas podem ficar **desatualizadas**. Verifica sempre as **fontes oficiais** antes de decisões técnicas ou comerciais.  
<br> Este material é fornecido “**AS IS**”, sem garantias. **Não** constitui aconselhamento jurídico, financeiro ou fiscal.

## O que vais encontrar
- 📚 **Catálogo de fornecedores**: `data/providers/*.yml` (produtos, integrações, links de doc, prazos de liquidação, taxas quando públicas, etc.)
- 🧭 **Guia de onboarding**: passos típicos (KYC/AML, contratos, testes, produção).
- ✅ **Checklist por fornecedor** (`docs/checklist-provider.md`)
- 🧩 **Esquema dos dados**: `data/schema.json` para validar entradas.
- 🔌 **Exemplos HTTP**: como pedir referências, webhooks, etc. em `examples/http`.

## Estrutura dos dados
Cada fornecedor é um `.yml` em `data/providers/` que segue o `data/schema.json`.

Exemplo rápido:
```yaml
# data/providers/exemplo-appx.yml
id: appx
nome: "AppX Pagamentos"
categoria: "agregador"   # ver data/categories.yml
canais:
  - referencia                # referencia/QR/pos/ecommerce/mobile_money
  - ecommerce
produtos:
  - "Pagamentos por referência"
  - "Checkout e-commerce"
documentacao:
  site: "https://exemplo.appx.ao"
  docs_api: "https://exemplo.appx.ao/dev/docs"
  portal_merchant: "https://exemplo.appx.ao/merchant"
integracao:
  autenticacao: "API Key"
  webhooks: true
  sandbox: true
  linguagens_suportadas: ["PHP", "JavaScript", "Java"]
financeiro:
  moedas: ["AOA"]
  liquidacao:
    prazo: "D+2"
    tipo: "transferência bancária"
  taxas:
    fixo_aoa: null
    percentual: null
compliance:
  pci_dss: "Afirmado pelo fornecedor"   # ou "Desconhecido"
  kyc: "Contrato + NIF + IBAN + docs societários"
cobertura:
  paises: ["Angola"]
contacto:
  email: "parcerias@exemplo.appx.ao"
  telefone: "+244 xxx xxx xxx"
estado_info: "parcial"                   # parcial/confirmada/obsoleta
fontes:
  - "https://exemplo.appx.ao/dev/docs"
observacoes: "Notas úteis para devs."

```
# Contribuir

Obrigado por quereres ajudar! Segue estes passos:

1. **Escolhe a categoria** do fornecedor (ver `data/categories.yml`).
2. **Cria um YAML** em `data/providers/` segundo `data/schema.json`.
3. **Inclui fontes** públicas (docs oficiais, páginas de preços, FAQs).
4. **Assinala `estado_info`**: `parcial`, `confirmada` ou `obsoleta`.
5. **Abre o PR** usando o template. Mantém um tom respeitoso e factual.

### Estilo
- Português (Angola) por defeito; aceita-se EN como alternativa.
- Evitar afirmações sem fonte (“ouvir dizer”, grupos de WhatsApp, etc.).
- Nada de logótipos/imagens sem permissão.

### Validação (opcional mas recomendado)
- Usa um validador JSON Schema para conferir `data/schema.json`. (docs/dados): CC BY 4.0 → LICENSES/LICENSE-CONTENT-CC-BY-4.0.md

# Código de Conduta 
- Sê respeitoso, inclusivo, paciente.
- Debate técnico ≠ ataque pessoal.
- Zero tolerância a assédio, discriminação ou spam.
- Moderadores podem editar/remover conteúdo fora das regras.

# Segurança 
Se identificares informação sensível (chaves, credenciais, endpoints internos), **não** abras issue pública.  
Envia um email para o maintainer (abre um issue vazio pedindo contacto). Removeremos rapidamente.