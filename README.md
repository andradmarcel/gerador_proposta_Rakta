# Gerador de Propostas Rakta Lab

Um gerador interativo de propostas comerciais de alta performance em formato PDF (apresentação widescreen 16:9), adaptado visualmente ao site **rakta.digital** e equipado com IA para personalização de escopos.

## 🚀 Como Executar

Este aplicativo foi projetado com **zero dependências**. Você não precisa instalar o Node.js, Python ou qualquer servidor local para usá-lo.

1. Navegue até a pasta do projeto no seu explorador de arquivos:
   `C:\Users\Marcel\Documents\gerador_proposta_rakta`
2. **Dê um duplo clique no arquivo `index.html`**.
3. O aplicativo abrirá imediatamente no seu navegador padrão (Google Chrome, Microsoft Edge, Brave, etc.).

---

## 🛠️ Recursos do Gerador

A interface é dividida em dois painéis (Split-Screen) com os seguintes recursos:

### 1. Painel de Controle (Esquerda)
*   **Identificação**: Digite o nome do cliente, título da proposta e validade (a data limite é recalculada de forma automatizada).
*   **Nicho do Cliente**: Escolha entre nichos populares (*E-commerce*, *SaaS B2B*, *Saúde & Clínicas*, *Negócios Locais*, etc.) para auto-carregar as **Dores do Diagnóstico** e a **Estratégia Recomendada** (totalmente editáveis).
*   **Inteligência Artificial (Gemini)**:
    *   Insira sua API Key do Gemini (com máscara de senha e botão para mostrar/ocultar a chave).
    *   A chave é salva de forma segura no navegador (`localStorage`) para uso futuro.
    *   Botão **"✨ Adaptar Escopos ao Nicho com IA"**: Envia as entregas dos serviços selecionados para o modelo `gemini-3.1-flash-lite`, reescrevendo os bullet points de forma comercialmente persuasiva e focada no nicho do cliente, sem alterar os limites numéricos originais.
*   **Escopo de Serviços Dinâmico (Option A)**:
    *   As categorias do accordion iniciam limpas.
    *   Selecione serviços através de um dropdown **`+ Adicionar Serviço...`** dentro de cada categoria.
    *   Ao adicionar, um card de customização elegante é criado abaixo do dropdown, permitindo escolher o **Nível** (*Entrada, Intermediário, Avançado*), ajustar o **Preço Principal**, **Mensalidade** (se houver) e editar o **Escopo da Entrega**.
    *   O dropdown oculta as opções já selecionadas e permite restaurá-las caso o serviço seja removido clicando na **Lixeira**.
*   **Condições Comerciais**: Ajuste prazo contratual, termos comerciais e setups.
*   **Slides Inclusos**: Toggles para habilitar ou desabilitar slides individuais no PDF final.

### 2. Preview em Tempo Real (Direita)
*   Visualização das páginas da proposta comercial sobrepostas milimetricamente com os dados editados.
*   **Ocultação de Preços Individuais**: Todos os preços individuais de serviços são ocultados no escopo e na tabela de resumo do plano, marcando-os apenas como `✓ Incluso` e exibindo os totais acumulados mensais e únicos no rodapé.
*   **Páginas Extras Automatizadas (Slide 7)**: O sistema agrupa e divide o escopo de serviços de 3 em 3 em múltiplos slides dinâmicos para evitar estouro de páginas.
*   **Slide de Fechamento Limpo**: O rodapé de dúvidas e contatos foi rebaixado para evitar sobrepor a grade de marcas oficiais da Rakta.

---

## 📄 Geração e Exportação de PDF

Ao clicar no botão vermelho **"Gerar Proposta em PDF"**:
1. O script compila as páginas em tamanho real em formato widescreen de pontos (`720pt x 405pt`), que equivale exatamente à resolução CSS de `960px x 540px` (proporção 16:9).
2. O renderizador utiliza as configurações `useCORS: true` e `allowTaint: false` para puxar com segurança fontes e ícones externos CDN sem corromper a compilação.
3. A renderização é efetuada em um container em memória (DOM desconectado), eliminando bugs comuns de posicionamento absoluto (`left: -9999px`) e gerando arquivos nítidos com **DPI duplo (escala 2x)**.
4. O download inicia de forma automatizada com o nome `proposta-rakta-[nome-do-cliente].pdf`.
