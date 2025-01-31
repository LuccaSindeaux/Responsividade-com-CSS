# Responsividade-com-CSS
Treinando responsividade de sites com CSS.

Box-sizing:
box sizing impede que, quando um borda solida de pelo menos 1px é adicionado à algum elemento, as bordas ultrapassem o tamanho máximo daquele elemento. Por exemplo, sem utilizar o box-sizing:border-box, uma div de tamanho 100px com uma borda de 2px vai aparcer em inspecionar elemento com tamanho de 102px; quando a propriedade é devidamente utilizada, a borda não cresce para fora do elemento (div), mas sim para dentro, mantendo o tamanho original de 100px.

Position: relative:
Propriedade do CSS normalmente uitlizadas em divs ou outros elementos que possuem um outro elemento pai, isto é, estão inseridos dentro de um elemento maior. Ao dizer que a posição é relativa, estamos dizendo que todas as modificações que fazemos com CSS naquele elemento está alterando em relação ao seu elemento pai. Se colocarmos uma div com texto dentro de um tag section, e declaramos o position relative e falamos que ela possui um top de 50%, isto significa que a div alterada irá se mover para baixo 50% do tamanho de seu elemento pai. Quanto maior for a altura do elemento pai, mais ela andará, mas sempre será 50%.   

Unidades de medida:
O pixel é a unidade mais conhecida, mas sempre usar ele em sites pode acabar causando problemas. Existem outras unidades, como o "rem". Cada Rem é equivalente a 16px, que é o tamanho padrão da fonte avulsa no html. Contudo isto pode ser alterado. Se eu defino no meu CSS que:
        html{
            font-size:10px;
        }
    Sigifica que a partir deste momento, todos os os meus rem equivalem a 10px, portanto 2rem=20px, 3rem=30px, etc.
    Além do rem, há o "em". O rem pega uma medida na "raiz" do código, como no exemplo, definindo o tamanho universal é o que define o valor do rem. O em é relativo a tag mais próxima. Digamos que eu crie uma div com o atributo style embutido nela:
        <div style='font-size: 10px;'>
            <p style='font-size: 2em;'>Aqui neste parágrafo os caracteres terão 20px, pois estão usando de referência o font size definido na div pai desta tag p.</p>
        </div>

View Width e View Height (vw e vh):
Unidades de medida extremamente importantes quando estamos falando de respoonsividade. Elas são definidas baseadas no tamanho da tela que está sendo vista. Se uma tela possui largura de 1000px, quer dizer que 1vw=10px. Isto é, 1vw=1% do tamanho da tela usada para visualização. O mesmo conceito se aplica para vh, porém ele se refere à altura. 

Animações:
Em CSS existem os Transitions. São quatro propriedades que trazem animações aos elementos. São eles:
1) transition-property: opacity;  --> referente normalmnte a um hover, quando passamos o mouse por cima.
2) transition-duration: 0.5s;     --> determina o quanto dura uma transição.
3) transition-timing-function: ease-in-out --> determina COMO uma transição será mostrada.
4) transition-delay: 0.5s;        --> determina o atraso que uma transição terá anmtes de ocorrer
Uma tag com as alterações do exemplo será opaca quando o mouse passar por cima (1); terá uma tarnsição que durará meio segundo (2) que será feita de forma suave, e ela sairá de forma também suave quando tirarmos o mouse de cima dela (3); mas ela demorará meio segundo para iniciar e terminar(4).
Tudo isto ser escrito de uma forma só numa única linha:
    button{
        transition: opacity 0.5s ease-in-out 0.5s;
    } Não são necessários escrever todos os valores, se por exemplo, não existir ym delay desejado, o último valor não é necessário.

Selecionando elementos pares e ímpares:
A propriedade nth-child(even) seleciona elementos pares, e a nth-child(odd) seleciona os ímpares. Eis o exemplo com HTML e CSS:
Se eu desejo que por exemplo, a segunda tag article seja colocada ao contrário (botão primeiro) eu teria um CSS:
    .alfa{
        display: flex;
        flex-direction: row;
}
    .alfa:nth-child(even){
        flex-direction: row-reverse;
}
Deste jeito somente os pares serão alterados, neste caso, somente o segundo article com class alfa.


GRID:
Quando definimos que o display é grid, temos que definir como será o template, isto é, a organização:
.gridContainer{
    display: grid;
    grid-template-columns: repeat(3, 1fr); ---> sinaliza que serão três colunas com um elemento em cada. 
}

GRID AREA:
Ao definir que um grid está numa área, estamos "jogando batalha naval" com o código, definindo onde está cada elemento numa linha e numa coluna, como visto na seção de empresas parceiras do código:

        .gridContainer{
            display: grid;
            grid-template-columns: repeat(3, 1fr); 
            gap:5rem
        }
        .gridContainerCompany{
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            grid-template-rows: repeat(3, 1fr);
            gap: 1.5rem;
            margin-top: 3rem;
        }
        .comp1{
            grid-area: 3 / 1;
        }
        .comp2{
            grid-area: 2 / 2 ;
        }
        .comp3{
            grid-area: 3 / 2 ;
        }
        .comp4{
            grid-area: 1 / 3 ;
        }
        .comp5{
            grid-area: 2 / 3 ;
        }
        .comp6{
            grid-area: 3 / 3;
        }
        .comp7{
            grid-area: 2 / 4;
        }
        .comp8{
            grid-area: 3 / 4;
        }
        .comp9{
            grid-area: 3 / 5;
        }



Portabilidade e Responsividade:
A tag meta que aparece no VScode quando criamos a tag html:5 é a responsável pela portabilidade (viewport). Existem tamanhos considerados padrões para desenvolvimento de telas responsivas:
                - Desktop: X >= 1024px
                - Tablet:  X >= 768px
                - Mobile   X < 768px
A alteração da portabilidade em sites é feita via CSS com a ferramenta @media, usadas para criação de Media Queries, com ela alteramos todas as propriedades de nosso site fentro dela como visto no final do código de CSS onde o projeto goi portado para tablet e mobile.