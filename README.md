
---
# Aula 12 - Programação Web

## 🚀 Tutorial: Criando um Site com Componentes Reutilizáveis (Vanilla JS)

Neste projeto, vamos aprender como criar elementos de uma página web (como menus e cards) que podem ser reaproveitados em várias páginas sem a necessidade de copiar e colar o mesmo código HTML várias vezes.

## 📁 Passo 1: Organizando a Estrutura do Projeto

Primeiro, crie uma pasta no seu computador para o projeto. Dentro dela, crie **5 arquivos** com os seguintes nomes exatos:

* `index.html` (Página Inicial)
* `produtos.html` (Página de Produtos)
* `contato.html` (Página de Contato)
* `style.css` (Estilo visual)
* `script.js` (Lógica dos componentes)

---

## 🎨 Passo 2: O Visual do Site (`style.css`)

Abra o arquivo `style.css` e adicione o código abaixo. Ele será responsável por deixar nosso menu alinhado, os botões com efeitos visuais ao passar o mouse (*hover*) e os cards organizados.

```css
/* Estilo geral dos parágrafos de destaque */
.paragrafo {
    padding: 20px;
    border-radius: 10px;
    background-color: #f4f4f4;
    text-align: center;
    font-family: Arial, sans-serif;
}

/* Estrutura do Menu de Navegação */
#menu {
    display: flex;
    justify-content: center;
    gap: 15px;
    margin-bottom: 30px;
}

/* Botões do Menu */
.botao-menu {
    padding: 12px 20px;
    border-radius: 8px;
    background-color: #222;
    color: white;
    text-decoration: none;
    font-size: 16px;
    font-family: Arial, sans-serif;
    transition: 0.3s;
}

/* Efeito ao passar o mouse nos botões */
.botao-menu:hover {
    background-color: #0077ff;
    transform: scale(1.05);
}

/* Container onde os cards vão aparecer */
#conteudo {
    display: flex;
    justify-content: center;
    margin-top: 50px;
}

/* Estilo do Card */
.card {
    width: 300px;
    padding: 20px;
    border-radius: 10px;
    background-color: #f4f4f4;
    box-shadow: 0 0 10px rgba(0,0,0,0.2);
    text-align: center;
    font-family: Arial, sans-serif;
}

.card h2 {
    margin-bottom: 10px;
    color: #222;
}

```

---

## ⚙️ Passo 3: A Lógica dos Componentes (`script.js`)

Aqui acontece a mágica! Em vez de escrever o menu em todas as páginas, criamos uma função em JavaScript que gera o HTML do menu e o insere nas páginas de forma dinâmica.

```javascript
// 1. Função que cria a estrutura HTML de um botão do menu
function criarBotaoMenu(texto, link){
    return ` 
        <a href="${link}" class="botao-menu">
            ${texto}
        </a>
    `;
}

// Captura a tag <nav id="menu"> do HTML
const menu = document.getElementById("menu");

// Insere os botões dentro do menu automaticamente em qualquer página que use este script
menu.innerHTML += criarBotaoMenu("Início", "index.html");
menu.innerHTML += criarBotaoMenu("Produtos", "produtos.html");
menu.innerHTML += criarBotaoMenu("Contato", "contato.html");


// 2. Função que cria a estrutura HTML de um Card
function criarCard(titulo, texto){
    return `
        <div class="card">
            <h2>${titulo}</h2>
            <p>${texto}</p>
        </div>
    `;
}

// Captura a <div id="conteudo"> do HTML para usarmos nas páginas
const conteudo = document.getElementById("conteudo");

```

---

## 🌐 Passo 4: Criando as Páginas HTML

Agora vamos criar as três páginas. Repare que todas elas possuem a mesma estrutura básica: chamam o `style.css`, têm uma `<nav id="menu"></nav>` vazia, uma `<div id="conteudo"></div>` vazia e chamam o `script.js` no final.

### 🏠 Página Inicial (`index.html`)

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Componentes Reutilizáveis</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <nav id="menu"></nav>

    <p class="paragrafo">Essa é a página Inicial</p>

    <div id="conteudo"></div>

    <script src="script.js"></script>
    <script>
        // Personalizando o card desta página
        conteudo.innerHTML = criarCard("Legião Urbana", "Índios");
    </script>
</body>
</html>

```

### 📦 Página de Produtos (`produtos.html`)

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Componentes Reutilizáveis</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <nav id="menu"></nav>

    <p class="paragrafo">Os Melhores Produtos</p>

    <div id="conteudo"></div>

    <script src="script.js"></script>
    <script>
        // Personalizando o card desta página
        conteudo.innerHTML = criarCard("Conheça nossos produtos", "Muitas coisas");
    </script>
</body>
</html>

```

### 📞 Página de Contato (`contato.html`)

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Componentes Reutilizáveis</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <nav id="menu"></nav>

    <p class="paragrafo">Entre em contato</p>

    <div id="conteudo"></div>
   
    <script src="script.js"></script>
     <script>
        // Personalizando o card desta página
        conteudo.innerHTML = criarCard("Contatos", "Nosso e-mail: ecit@email.com");
    </script>
</body>
</html>

```

---

## >>> Desafios Práticos <<<

Agora que o projeto está funcionando, faça as seguintes alterações para testar seus conhecimentos:

* **Desafio 1 (CSS):** Mude a cor de fundo dos botões do menu quando o mouse passa por cima. No `style.css`, altere a propriedade `background-color` dentro de `.botao-menu:hover` para a sua cor favorita (ex: `tomato`, `purple`, `#2ecc71`).
* **Desafio 2 (JavaScript & Reutilização):** Imagine que o site agora precisa de uma página "Sobre nós".
1. Crie um arquivo chamado `sobre.html` (siga a mesma estrutura das outras páginas).
2. Vá no arquivo `script.js` e adicione uma nova linha para o botão "Sobre": `menu.innerHTML += criarBotaoMenu("Sobre", "sobre.html");`.
3. *Reflexão:* Note que o botão apareceu automaticamente em **todas** as páginas do site, sem você precisar mexer no HTML de cada uma delas!


* **Desafio 3 (Conteúdo):** Modifique o texto e o título dos cards dentro dos blocos `<script>` de cada arquivo HTML para exibir informações que você desejar.
