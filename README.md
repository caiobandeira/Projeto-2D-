# Transformações Geométricas 2D — Cena de uma cidade

Trabalho da disciplina de Computação Gráfica.

**Alunos:** Caio De Araujo e Guilherme Marques

## Como executar

É um arquivo único, sem bibliotecas e sem servidor. Basta abrir o `index.html`
em qualquer navegador (Chrome, Firefox ou Edge).

## Descrição da cena

Uma rua de cidade desenhada em Canvas 2D, com sol, prédios, catavento,
dois carros circulando e um guindaste de braço articulado.

## Controles

| Tecla / mouse | O que faz |
|---|---|
| Seta direita / esquerda | Aumenta e diminui a velocidade dos carros |
| Seta cima / baixo | Gira o braço do guindaste |
| A / S | Gira o antebraço do guindaste |
| Espaço | Pausa a animação |
| Clique no desenho | Inverte o sentido do trânsito (os carros são espelhados) |

## Requisitos obrigatórios

| Requisito | Onde está | Função no código |
|---|---|---|
| Translação (`ctx.translate`) | Movimento dos carros na rua | `desenharCarro` |
| Rotação (`ctx.rotate`) | Rodas dos carros e pás do catavento | `desenharRoda`, `desenharCatavento` |
| Escala (`ctx.scale`) | Tamanho dos carros e o sol que pulsa | `desenharCarro`, `desenharSol` |
| Composição de transformações | O carro combina translação, reflexão e escala, e as rodas giram dentro dele | `desenharCarro` |
| Rotação/escala com ponto fixo (T → Op → T) | Pás do catavento, raios e disco do sol | `desenharCatavento`, `desenharSol` |
| Animação com `requestAnimationFrame` | Loop principal, com `setTransform` resetando a matriz a cada quadro | `animar` |
| `save` / `restore` | Cada objeto é desenhado dentro de um par `save`/`restore` | todas as funções de desenho |

## Requisitos bônus

| Bônus | Onde está |
|---|---|
| Interatividade com teclado e mouse | Eventos `keydown` e `click` no fim do arquivo |
| Reflexão | `ctx.scale(-1, 1)` nos carros quando o sentido é invertido (`desenharCarro`) |
| Cisalhamento | `ctx.transform(1, 0, -0.7, 1, 0, 0)` nas sombras dos prédios (`desenharPredio`) |
| Hierarquia de transformações | Guindaste: torre → braço → antebraço → cabo com a caixa (`desenharGuindaste`) |

## Observações

O guindaste é o exemplo de hierarquia: cada parte é desenhada no sistema de
coordenadas da parte anterior, então girar o braço leva junto o antebraço, o
cabo e a caixa. No último nível o cabo aplica a rotação inversa
(`-anguloBraco1 - anguloBraco2`) para continuar pendurado na vertical.
