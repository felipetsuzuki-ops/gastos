# 💸 GastoAI

Gerenciador de gastos pessoais com reconhecimento de voz, funcionamento offline e sincronização com Google Drive. Desenvolvido como um único arquivo HTML — sem dependências, sem servidor, sem instalação.

**[→ Abrir o App](https://SEU_USUARIO.github.io/gastoai)**

---

## ✨ Funcionalidades

### 📝 Registro por Voz ou Texto
- Fale ou escreva o gasto em linguagem natural: *"gastei 85 reais no mercado"*
- Interpretação local por regras em português — sem API externa, sem internet
- Detecta automaticamente valor, categoria e descrição
- Card de confirmação com campos editáveis antes de salvar
- Chips de exemplos rápidos para testar

### 📊 Relatórios
- Filtros por período: 7 dias, 30 dias, 3 meses, 1 ano
- Gráfico de barras com evolução dos gastos no período
- Insights: total gasto, média diária, quantidade de lançamentos, maior categoria
- Breakdown de gastos por categoria
- Exportar dados em **CSV** (para Excel/Sheets) e **JSON** (backup completo)
- Importar JSON para restaurar ou migrar dados

### ☁️ Google Drive
- Sincroniza os dados com um arquivo `gastoai-backup.json` na sua conta Google
- Restaurar backup de qualquer dispositivo com o mesmo Google
- Indicador de status de sincronização em tempo real

### 📱 PWA — Instalar no iPhone
- Funciona como app nativo na tela inicial
- 100% offline após o primeiro carregamento
- Dados persistidos no `localStorage` do dispositivo

---

## 🚀 Como usar no iPhone

1. Acesse a URL do app pelo **Safari**
2. Toque em **Compartilhar** (ícone de caixa com seta)
3. Selecione **"Adicionar à Tela de Início"**
4. O app aparece como ícone, sem barra do navegador

### Reconhecimento de voz
- O botão 🎤 usa a Web Speech API nativa do Safari/iOS
- Alternativa mais confiável: toque no campo de texto e use o **🎤 do teclado iOS** (ditado nativo da Apple)

---

## ⚙️ Configurar Google Drive

### 1. Criar projeto no Google Cloud

1. Acesse [console.cloud.google.com](https://console.cloud.google.com)
2. Crie um novo projeto (ex: `GastoAI`)
3. Vá em **APIs & Services → Library**
4. Busque por **Google Drive API** e clique em **Enable**

### 2. Criar credencial OAuth

1. Vá em **APIs & Services → Credentials**
2. Clique em **Create Credentials → OAuth 2.0 Client ID**
3. Tipo: **Web Application**
4. Em **Authorized JavaScript origins**, adicione:
   ```
   https://SEU_USUARIO.github.io
   ```
5. Clique em **Create** e copie o **Client ID**

> O Client ID tem o formato: `000000000000-xxxxxxxxxxxxxxxx.apps.googleusercontent.com`

### 3. Ativar no app

1. Abra o app pelo GitHub Pages
2. Vá na aba **☁️ Nuvem**
3. Cole o Client ID no campo de configuração
4. Clique em **Salvar e recarregar**
5. Clique em **Entrar com Google**

---

## 🗂️ Categorias detectadas automaticamente

| Categoria | Palavras-chave detectadas |
|-----------|--------------------------|
| 🍔 Alimentação | mercado, restaurante, almoço, ifood, padaria, delivery... |
| 🚗 Transporte | gasolina, uber, taxi, ônibus, estacionamento, pedágio... |
| 💊 Saúde | farmácia, médico, dentista, academia, hospital, plano... |
| 🎬 Lazer | cinema, netflix, show, viagem, bar, festa, spotify... |
| 🏠 Moradia | aluguel, luz, água, internet, condomínio, gás... |
| 📚 Educação | escola, faculdade, curso, livro, mensalidade... |
| 👗 Vestuário | roupa, sapato, tênis, camisa, loja... |
| 📦 Outros | tudo que não se encaixa acima |

---

## 🏗️ Estrutura do projeto

```
gastoai/
├── index.html      # App completo — tudo em um único arquivo
└── README.md
```

Não há dependências externas além de:
- **Google Fonts** (Syne + DM Mono) — carregadas online, com fallback local
- **Google Identity Services** (`accounts.google.com/gsi/client`) — apenas para o login com Google
- **Google Drive REST API** — apenas quando sincronizar

---

## 💾 Formato dos dados

Os dados ficam salvos no `localStorage` do navegador com a chave `gastoai_v2`, e no Google Drive como `gastoai-backup.json`.

Estrutura de cada lançamento:

```json
{
  "id": 1718123456789,
  "desc": "Mercado",
  "amount": 85.00,
  "category": "alimentacao",
  "date": "19/04/2026"
}
```

---

## 🔒 Privacidade

- Nenhum dado é enviado a servidores externos
- A interpretação do texto é feita **100% localmente** no dispositivo
- O Google Drive é acessado diretamente pela sua conta — os dados pertencem a você
- O Client ID OAuth é armazenado apenas no `localStorage` do seu navegador

---

## 📄 Licença

MIT — use, modifique e distribua à vontade.
