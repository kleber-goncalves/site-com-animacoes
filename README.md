# 🏎️ FP Selection - Slider Animado de Carros

Este projeto é um **slider (carrossel) de carros esportivos** focado em demonstrar **animações fluidas e estilizadas** utilizando **HTML**, **CSS** e **JavaScript** puro. O principal objetivo foi criar uma transição visualmente atraente e dinâmica entre os itens, com destaque para a manipulação de propriedades CSS via JavaScript para orquestrar as animações de entrada e saída.

O projeto utiliza um design inspirado em temas de **supercarros**, com cores fortes (roxo, preto, verde neon) e tipografia impactante.

---

### 🌟 Funcionalidades Principais

* **Slider de Conteúdo:** Exibe uma lista de carros (Porsche, Ferrari, Lamborghini) com suas imagens e descrições.
* **Animação Controlada por JavaScript e CSS:**
    * As transições dos slides e dos elementos de conteúdo (texto, imagem) são animadas usando a propriedade `transform` no CSS, com a variável `--calculation` sendo definida via JavaScript.
    * Isso permite controlar a direção da animação (entrada pela esquerda ou direita) de forma dinâmica.
* **Navegação por Botões:** Botões de "Anterior" (`prev`) e "Próximo" (`next`) para navegar entre os slides.
* **Indicadores Visuais:**
    * Pontos (`dots`) para mostrar qual slide está ativo.
    * Um contador de número formatado (`01`, `02`, etc.).

---

### 🛠️ Estrutura do Projeto

O projeto é composto por três arquivos principais:

1.  **`index.html`**: A estrutura base do HTML. Define o *layout* principal, o *header*, a seção do *slider* (`<section class="container">`) e inclui os *links* para o CSS e JavaScript.
2.  **`style.css`**: Contém todos os estilos e regras de animação. É o coração visual do projeto.
3.  **`script.js`**: A lógica de interação do slider. Responsável por lidar com os eventos de clique, atualizar o slide ativo e controlar a direção da animação via CSS.

---

### ⚙️ Detalhes Técnicos e Animação

#### 1. CSS (`style.css`)

O CSS utiliza a **variável customizada** `--calculation` para determinar a direção do movimento dos slides:

* Quando `--calculation` é **`1`** (próximo slide), os elementos saem para a esquerda e o novo slide entra da direita.
* Quando `--calculation` é **`-1`** (slide anterior), os elementos saem para a direita e o novo slide entra da esquerda.

**Exemplo de Estilo de Animação:**

```css
section {
    & .list {
        --calculation: 1; /* Definido dinamicamente pelo JS */

        & .item {
            /* Regra aplicada a todos os slides, exceto o ativo */
            transform: translateX(calc(-100vw * var(--calculation)) );
            transition: 0.5s;
            opacity: 0;

            & .content {
                & .car-information, h2, .description, .information {
                    /* Movimento do conteúdo (textos) */
                    transform: translateX(calc(-200px * var(--calculation)));
                    transition: 0.7s;
                    opacity: 0;
                }
            }
        }

        & .active {
            /* Regra aplicada apenas ao slide ativo */
            transform: translateX(0); /* Posição central */
            opacity: 1;
            /* Outras regras de transform para o conteúdo */
        }
    }
}

```
---


#### 2. JavaScript (script.js)

O JavaScript coordena a navegação e a ativação das classes CSS.

**Lógica de Navegação Principal:**
```JavaScript
nextButton.onclick = () => {
    // Define a variável CSS para animação de 'próximo' (entrada da direita)
    list.style.setProperty("--calculation", 1); 
    
    // Atualiza o índice, voltando para 0 se for o último
    active = active + 1 > lastPosition ? 0 : active + 1; 
    
    setSlide();
    items[active].classList.add("active");
};

prevButton.onclick = () => {
    // Define a variável CSS para animação de 'anterior' (entrada da esquerda)
    list.style.setProperty("--calculation", -1);
    
    // Atualiza o índice, voltando para o último se for o primeiro
    active = active - 1 < firstPosition ? lastPosition : active - 1;
    
    setSlide();
    items[active].classList.add("active");
};
```
---

### Como Executar
1. 🚀**Obtenha os Arquivos:** Certifique-se de ter os arquivos `index.html`, `style.css` e `script.js` na mesma pasta.

2. **Imagens:** O projeto faz referência a imagens (Ex: `./img/1.png`, `./img/logo.png`, `./img/arrow.svg`). Você precisará criar uma pasta img e adicionar imagens de placeholders ou as imagens reais para que o layout seja exibido corretamente.

3. **Abra no Navegador:** Abra o arquivo `index.html` em qualquer navegador moderno.
---
📝 Créditos e Licença
- Desenvolvedor: (Seu Nome/Nome da Equipe)

- Licença: (Adicione sua licença preferida, ex: MIT)
