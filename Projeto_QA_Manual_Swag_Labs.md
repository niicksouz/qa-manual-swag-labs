# Projeto de QA Manual — Swag Labs

**Responsável:** Monick Lichtenheld  
**Data da execução:** 14/10/2026  
**Ambiente:** Sauce Demo (Swag Labs), computador desktop; navegador não confirmado  
**Tipo:** Projeto de estudo, teste manual exploratório

## Objetivo

Exercitar testes manuais de um fluxo de e-commerce de demonstração, verificando login, carrinho, checkout, validações de formulário e geração do comprovante. Os resultados refletem a execução observada neste ambiente e não representam experiência profissional.

## Escopo

- Login com credenciais válidas
- Adicionar e remover produtos do carrinho
- Conferir dados e valores no checkout
- Validar campos obrigatórios
- Observar validação do código postal
- Concluir a compra de demonstração e gerar PDF

## Casos executados

| ID | Cenário | Resultado observado | Status |
|---|---|---|---|
| TC-LOGIN-001 | Entrar com credenciais válidas | Acesso concedido e catálogo exibido | Aprovado |
| TC-CART-001 | Adicionar Sauce Labs Onesie e Sauce Labs Backpack | Os produtos, descrições e preços corresponderam aos itens adicionados | Aprovado |
| TC-CHECKOUT-001 | Avançar para o resumo após preencher os dados | O resumo exibiu os produtos, valores, impostos, entrega e informação de pagamento; após repetir o fluxo, abriu normalmente | Aprovado no reteste |
| TC-CHECKOUT-002 | Deixar código postal vazio | O avanço foi bloqueado e o sistema informou que o campo era obrigatório | Aprovado |
| TC-CHECKOUT-003 | Deixar primeiro nome vazio | O avanço foi bloqueado e o sistema pediu o primeiro nome | Aprovado |
| TC-CHECKOUT-004 | Deixar sobrenome vazio | O avanço foi bloqueado e o sistema pediu o sobrenome | Aprovado |
| TC-CHECKOUT-005 | Inserir letras no código postal (ABCDE) | O valor foi aceito | Observação: regra de formato não especificada |
| TC-CHECKOUT-006 | Concluir a compra de demonstração | A tela Checkout: Complete! confirmou a conclusão e apresentou opções para voltar à loja e gerar PDF | Aprovado |
| TC-PDF-001 | Gerar comprovante PDF | O comprovante apresentou corretamente compra, endereço de envio, nome do comprador e totais com imposto, conforme conferência manual | Aprovado |
| TC-CART-002 | Remover um produto e avançar ao checkout | O resumo exibiu apenas o item mantido no carrinho | Aprovado |
| TC-CART-003 | Conferir recálculo após remoção | Subtotal, imposto e total foram recalculados corretamente, conforme conferência manual | Aprovado |

## Observações exploratórias

1. **Imagens no carrinho:** a tela exibiu quantidade, nome, descrição e preço, mas não as imagens dos produtos. Registrar como sugestão de usabilidade, pois não foi encontrado requisito que determine a exibição de miniaturas.
2. **Código postal:** o formulário aceitou ABCDE e também 00000. Sem país ou regra de formato indicada na tela, isso não é classificado como defeito confirmado. Para um produto direcionado ao Brasil, por exemplo, seria necessário definir validação compatível com CEP.
3. **Informação de pagamento:** o resumo mostrou “SauceCard #31337” sem uma etapa para selecionar pagamento. Tratado como comportamento da loja de demonstração; em uma loja real, os requisitos de pagamento e a forma segura de apresentar os dados precisariam ser definidos.
4. **Redirecionamentos para login:** durante a execução, houve redirecionamento para a tela de login com a mensagem “You can only access '/checkout-step-two.html' when you are logged in.” Após novo login, os itens permaneceram no carrinho e o fluxo foi concluído. Causa não confirmada; manter como observação intermitente e retestar.

## Limitações

- Execução manual em uma sessão e em um computador; navegador e versão não foram confirmados.
- A loja é um ambiente de demonstração. Dados de pagamento, entrega e compra são simulados.
- As verificações de valores foram relatadas pela testadora; os valores exatos não foram transcritos para este relatório.
- As observações de interface não foram comparadas com uma especificação formal do produto.

## Próximos passos

- Repetir o fluxo para investigar os redirecionamentos de sessão.
- Definir um país-alvo e critérios claros antes de classificar a aceitação de códigos postais como defeito.
- Se desejar ampliar o portfólio, acrescentar casos para ordenação de produtos, remoção no próprio carrinho, campos inválidos e compatibilidade em outro navegador.
