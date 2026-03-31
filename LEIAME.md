# 🌻 Girassol PWA — Guia de Instalação

## O que é uma PWA?
Uma **Progressive Web App** funciona como um app nativo no celular, mas é instalada pelo navegador — sem precisar de Play Store.

---

## 📁 Arquivos do projeto

```
📂 pwa-girassol/
├── index.html      ← App principal (tudo aqui)
├── manifest.json   ← Metadados do app
├── sw.js           ← Service Worker (offline + notificações)
├── icon-192.png    ← Ícone do app (você precisa adicionar!)
└── icon-512.png    ← Ícone grande (você precisa adicionar!)
```

---

## 🚀 Como instalar e usar

### Passo 1 — Hospedar os arquivos
A PWA precisa estar em um servidor HTTPS. Opções gratuitas:

| Serviço | Link | Dificuldade |
|---------|------|-------------|
| **Netlify Drop** | netlify.com/drop | ⭐ Mais fácil |
| **Vercel** | vercel.com | ⭐⭐ |
| **GitHub Pages** | pages.github.com | ⭐⭐ |

#### Netlify Drop (mais fácil):
1. Acesse [app.netlify.com/drop](https://app.netlify.com/drop)
2. Arraste a pasta `pwa-girassol` para a página
3. Seu site estará em `https://nome-aleatorio.netlify.app`

---

### Passo 2 — Adicionar ícones
Você precisa de dois arquivos de ícone (imagem do girassol):
- `icon-192.png` — 192×192 pixels
- `icon-512.png` — 512×512 pixels

**Dica:** Use um emoji 🌻 em [favicon.io/emoji-favicons](https://favicon.io/emoji-favicons/) e baixe os tamanhos necessários.

---

### Passo 3 — Instalar no celular (Android)

1. Abra o link do seu site no **Chrome**
2. Toque no menu (⋮) → **"Adicionar à tela inicial"**
3. Confirme — o app aparece na tela inicial como qualquer aplicativo!

### Passo 3 — Instalar no celular (iPhone)

1. Abra o link no **Safari**
2. Toque em **Compartilhar** (ícone de caixa com seta)
3. Role até **"Adicionar à Tela de Início"**
4. Confirme

---

### Passo 4 — Ativar notificações
1. Abra o app instalado
2. Toque na aba **🔔 Lembretes**
3. Escolha o horário desejado
4. Toque em **"Ativar Notificações"**
5. Permita quando o celular perguntar

> ⚠️ **iPhone**: Notificações push só funcionam em iPhones com iOS 16.4+ e o app deve ser instalado via Safari antes de ativar.

---

## ✏️ Personalizar o app

Abra o `index.html` e edite o bloco `CFG` no final do arquivo:

```javascript
const CFG = {
  nomePessoa:   "Nome da pessoa amada",
  dataEspecial: new Date(2026, 3, 20, 0, 0, 0), // 20 abril 2026
  //             ano,  mês(0=jan), dia
  
  texto1: "Primeiro parágrafo da carta...",
  texto2: "Segundo parágrafo da carta...",
  
  foto1:    "URL ou caminho da foto 1",
  foto2:    "URL ou caminho da foto 2",
  legenda1: "Legenda da foto 1",
  legenda2: "Legenda da foto 2",
  
  musicaURL: "URL do arquivo MP3",
};
```

---

## 🔔 Como funcionam as notificações

- O Service Worker (`sw.js`) agenda um timer para o horário escolhido
- Todos os dias no horário definido, uma notificação aparece com a contagem regressiva
- A mensagem muda conforme se aproxima a data:
  - 30+ dias: "X dias restantes"
  - 7 dias: "A data está chegando!"
  - 1 dia: "Falta 1 dia!"
  - No dia: "Chegou o dia! 🎉"

> **Importante:** O Service Worker precisa de HTTPS para funcionar. Em `localhost` também funciona para testes.

---

## 🛠️ Testar localmente

Se tiver Python instalado:
```bash
cd pwa-girassol
python3 -m http.server 8080
```
Acesse: `http://localhost:8080`

Ou com Node.js:
```bash
npx serve .
```
