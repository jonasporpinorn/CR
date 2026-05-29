# Componentes Reutilizáveis
---

### 1. `script.js` (O Coração da Componentização)

```javascript
/**
 * COMPONENTE: Botão de Menu Reutilizável
 * Esta função gera a estrutura HTML de um link de navegação de forma dinâmica.
 * @param {string} texto - O nome que vai aparecer no botão (ex: "Início")
 * @param {string} link - O arquivo de destino para onde o botão aponta (ex: "index.html")
 */
function criarBotaoMenu(texto, link){
    // Utiliza Template Literals (crases ` `) para permitir quebras de linha e injeção de variáveis com ${}
    return ` 
        <a href="${link}" class="botao-menu" >
            ${texto}
        </a>
    `;
}

// Captura o elemento <nav id="menu"> do HTML onde os botões serão inseridos
const menu = document.getElementById("menu");

// Injeta os botões de navegação acumulando-os (+=) dentro do container do menu
// Se amanhã o cliente quiser uma página "Sobre", basta adicionar uma linha aqui!
menu.innerHTML += criarBotaoMenu("Início", "index.html");
menu.innerHTML += criarBotaoMenu("Contato", "contato.html");
menu.innerHTML += criarBotaoMenu("Produtos", "produtos.html");


/**
 * COMPONENTE: Card Reutilizável
 * Gera uma caixa de conteúdo padronizada (Card) que aceita informações diferentes para cada página.
 * @param {string} titulo - O título principal do Card
 * @param {string} texto - O texto descritivo/corpo do Card
 */
function criarCard(titulo, texto){
    return `
        <div class="card">
            <h2>${titulo}</h2>
            <p>${texto}</p>
        </div>
    `;
}

// Captura o elemento <div id="conteudo"> onde o conteúdo principal da página será exibido
const conteudo = document.getElementById("conteudo");

```

---

### 2. `index.html` (Página Inicial)

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

    <script src="script.js" ></script>

    <script>
        conteudo.innerHTML = criarCard(
            "Bem-Vindo", 
            "Esse é meu card Reutilizável"
        );
    </script>
</body>
</html>

```

---

### 3. `produtos.html` (Página de Produtos)

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

    <script src="script.js" ></script>

    <script>
        // Reutiliza o mesmo componente visual, mas com informações de produtos
        conteudo.innerHTML = criarCard(
            "Conheça nossos produtos",
            "Muitas coisas"
        );
    </script>
</body>
</html>

```

---

### 4. `contato.html` (Página de Contato)

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
   
    <script src="script.js" ></script>

     <script>
        // Reutiliza o card para exibir as informações de contato
        conteudo.innerHTML = criarCard(
            "Contatos",
            "Nosso e-mail: ecit@email.com"
        );
    </script>
</body>
</html>

```

---

### 5. `style.css` (Estilização dos Componentes)

```css
/* Estilo geral para os parágrafos de destaque de cada página */
.paragrafo {
    padding: 20px;
    border-radius: 10px;
    background-color: #f4f4f4;
    text-align: center;
}

/* Flexbox para alinhar os botões do menu horizontalmente e centralizados */
#menu {
    display: flex;
    justify-content: center;
    gap: 15px; /* Espaçamento de 15px entre os botões */
    margin-bottom: 30px;
}

/* Estilização base do botão de menu (gerado via script.js) */
.botao-menu {
    padding: 12px 20px;
    border: none;
    border-radius: 8px;
    background-color: #222; /* Cor de fundo escura */
    color: white;
    text-decoration: none; /* Remove o sublinhado padrão de links <a> */
    font-size: 16px;
    cursor: pointer;
    transition: 0.3s; /* Suaviza a transição de cor e efeito no hover */
}

/* Efeito visual ao passar o mouse sobre o botão do menu */
.botao-menu:hover {
    background-color: #0077ff; /* Muda o fundo para azul */
    transform: scale(1.05); /* Dá um leve zoom de 5% no botão */
}

/* Flexbox para centralizar o bloco do card na tela */
#conteudo {
    display: flex;
    justify-content: center;
    margin-top: 50px;
}

/* Estilização do componente de Card (gerado via script.js) */
.card {
    width: 300px;
    padding: 20px;
    border-radius: 10px;
    background-color: #f4f4f4;
    box-shadow: 0px 4px 6px rgba(0,0,0,0.1); /* Sombra suave para dar profundidade */
    text-align: center;
}

```

---
