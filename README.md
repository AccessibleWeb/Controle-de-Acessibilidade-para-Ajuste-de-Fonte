### **Documentação do Projeto: Controle de Acessibilidade para Ajuste de Fonte**

---

#### **Descrição do Projeto**

Este projeto é um exemplo funcional de um sistema de acessibilidade que permite aos usuários aumentar ou diminuir o tamanho da fonte do conteúdo de uma página web. A solução é desenvolvida com HTML, CSS e JavaScript, sendo otimizada para não afetar elementos específicos, como botões ou ícones de controle. 

O código garante que apenas os textos principais da página sejam ajustados, mantendo uma experiência de usuário intuitiva e acessível.

---

#### **Objetivos do Projeto**
1. **Acessibilidade:** Permitir que usuários com dificuldades visuais ajustem o tamanho da fonte para melhorar a legibilidade.
2. **Responsividade:** Garantir que o design e a funcionalidade permaneçam consistentes em diferentes dispositivos e tamanhos de tela.
3. **Isolamento de Estilo:** Prevenir que os controles de ajuste de fonte (botões e ícones) sejam afetados pelas alterações.

---

#### **Arquivos do Projeto**
1. **`index.html`**: Estrutura principal do código HTML.
2. **`style.css`**: Estilos personalizados aplicados aos elementos da página.
3. **`script.js`**: Função JavaScript responsável pelo ajuste de fonte.

---

### **Explicação Técnica do Código**

#### **HTML**
O HTML fornece a estrutura básica da página, incluindo os botões de controle fixos e o conteúdo de exemplo:

```html
<div class="controls">
    <button class="increase" onclick="changeFontSize('increase')">
        <span class="icon">+A</span>
    </button>
    <button class="decrease" onclick="changeFontSize('decrease')">
        <span class="icon">-A</span>
    </button>
</div>
<h1>Controle de Fonte</h1>
<p>Este exemplo mostra como evitar que os botões personalizados sejam afetados pelo ajuste de fonte.</p>
<p>Os botões permanecem fixos no topo direito e não mudam de tamanho.</p>
```

- **Botões de Controle**:
  - **Classe `.controls`**: Agrupa os botões de controle para fácil posicionamento.
  - **Classes `.increase` e `.decrease`**: Diferenciam os botões de aumentar e diminuir a fonte.

#### **CSS**
O CSS estiliza os botões, assegurando que eles tenham um design consistente e interativo, enquanto impede que sejam afetados pelo script de ajuste de fonte.

```css
.controls {
    position: fixed;
    top: 10px;
    right: 20px;
    display: flex;
    gap: 5px;
    z-index: 1000;
}
.controls button {
    width: 40px;
    height: 50px;
    font-size: 16px !important;
    font-weight: bold;
    color: #fff;
    border: none;
    border-radius: 0 0 15px 15px;
    cursor: pointer;
    text-align: center;
    padding: 10px;
    transition: transform 0.2s, box-shadow 0.2s ease;
}
.controls button:hover {
    transform: translateY(-5px);
}
.controls button.increase {
    background: linear-gradient(135deg, #25D366, #1da851);
}
.controls button.decrease {
    background: linear-gradient(135deg, #FFA500, #FF7F00);
}
```

- **Borda Arredondada Inferior Esquerda**: `border-radius: 0 0 15px 15px;` mantém o estilo diferenciado.
- **Gradiente de Fundo**: `background: linear-gradient(...)` para estilizar os botões com cores específicas.
- **Tamanho Fixo dos Botões**: `font-size: 16px !important;` garante que o tamanho do texto dos botões não seja alterado.

#### **JavaScript**
O script permite ajustar o tamanho da fonte do texto da página, excluindo elementos específicos (botões e ícones).

```javascript
function changeFontSize(action) {
    const elements = document.querySelectorAll('body *:not(.controls button):not(.controls):not(.icon)');

    elements.forEach(element => {
        const currentSize = parseFloat(window.getComputedStyle(element).fontSize);
        const newSize = action === 'increase' ? currentSize + 2 : currentSize - 2;

        if (newSize >= 12 && newSize <= 20) {
            element.style.fontSize = newSize + 'px';
        }
    });
}
```

- **Seleção de Elementos**:
  - O seletor `body *:not(.controls button):not(.controls):not(.icon)` exclui os botões e ícones de controle.
- **Cálculo de Novo Tamanho**:
  - Obtém o tamanho atual da fonte com `window.getComputedStyle`.
  - Ajusta o tamanho com base na ação (`increase` ou `decrease`).
  - Aplica os limites de 12px a 20px.

---

### **Como Executar**

1. **Clonar o Repositório**
   ```bash
   git clone https://github.com/skylinenando/font-size-accessibility.git
   cd font-size-accessibility
   ```

2. **Abrir no Navegador**
   Abra o arquivo `index.html` diretamente em seu navegador.

---

### **Melhorias Futuras**

- Adicionar suporte para salvar as preferências do usuário no `localStorage`.
- Implementar um botão de "reset" para restaurar o tamanho da fonte ao padrão.
- Ampliar os controles de acessibilidade com ajustes de contraste e espaçamento entre linhas.

---

### **Licença**

Este projeto está licenciado sob a [MIT License](LICENSE).

---

Esta documentação explica cada detalhe do código e está pronta para ser postada no seu GitHub. 🚀
