# LP GAC AION Y — BeGreen

Landing page de captacao de leads: carregador para veiculo eletrico, energia
fotovoltaica e bateria de armazenamento. Formulario integrado ao RD Station.

## Estrutura

```
index.html          pagina (Design Component)
support.js          runtime necessario para o index.html
assets/             imagem de fundo e logos
api/lead.js         funcao serverless: recebe o form e envia ao RD Station
vercel.json         builds e rotas
```

## Publicar na Vercel

1. **GitHub** — crie o repositorio `lp-gac-aion-y` e envie estes arquivos
   (no site: *Add file -> Upload files*, arraste tudo, inclusive a pasta `assets`
   e a pasta `api`; depois *Commit changes*).
2. **Vercel** — *Add New -> Project -> Import Git Repository* -> `lp-gac-aion-y`.
   Framework Preset: **Other**. Nao altere Build/Output.
3. **Variavel de ambiente** (antes do primeiro deploy), em
   *Settings -> Environment Variables*:

   | Nome | Valor | Ambientes |
   |---|---|---|
   | `RD_API_KEY` | API Key publica do RD Station | Production, Preview, Development |

4. **Deploy**. A URL sai como `lp-gac-aion-y.vercel.app`.
5. Dominio proprio (opcional): *Settings -> Domains*.

A partir daqui, todo commit no GitHub republica o site automaticamente.

## Onde pegar a RD_API_KEY

RD Station Marketing -> *Integracoes* -> *API* -> **API Key** (chave publica de
conversao). E a mesma usada na outra landing page.

## Identificador da conversao

O evento chega ao RD Station como `lp-begreen-gac-aion-y`
(campo `conversion_identifier` em `api/lead.js`). Use esse nome ao montar
segmentacoes e automacoes.

## Campos enviados

Nome, e-mail, telefone, CPF/CNPJ, endereco, numero, cidade, estado, CEP,
tipo de local, modelo do veiculo, concessionaria GAC, consentimento de
comunicacao e parametros de UTM.

## Teste local (opcional)

```bash
npm i -g vercel
vercel dev
```

Crie um `.env.local` com `RD_API_KEY=...` para o formulario funcionar localmente.
