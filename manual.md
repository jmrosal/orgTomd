# Emacs + Orgmode + Latex => Markdown

Esse documento é um pequeno manual para quem quer produzir textos
científicos com fórmulas matemáticas e códigos de programação em
markdown a partir do editor de textos emacs. Assume-se alguma
familiaridade com as ferramentas utilizadas e o foco é
majoritariamente em "montar" o ambiente de trabalho para utilizá-lo
em desenvolvimento. Pouco ou nenhum esforço será dedicada à
explicação das ferramentas em si.

## Motivação

Emacs é um editor de texto cujos os princípio de produtividade e
universalidade dificilmente podem ser ultrapassados por outros
editores. De fato, esses princípios são muito bem representados em
seu modo "orgmode", que possibilita a edição de textos, fórmulas
matemáticas e código de programação - inclusive com o resultado de
sua computação em caso de linguages interpretadas - simultaneamente
em um único documento em formato texto.

Além disso, o documento pode ser exportado nativamente para vários
outros formatos, incluindo aí arquivos markdown, html, entre
outros. No caso particular do programa *latex*, quando o orgmode
estiver ativado, pode-se digitar a expressão tal como faríamos em
documento ".tex", isto é:

    \begin{align*}
    y = \alpha + \beta + \epsilon
    \end{align*}

Depois disso, através da máquina de exportação de formatos
apropriada, a equação será gerada, novamente tal como se estivesse
em um ambiente de desenvolvimento latex.

Certamente, há outras alternativas para editação de arquivos
markdown dentro do ambiente emacs que possam até ser ainda mais
eficientes do que aquela proposta aqui. No entanto, por questão de
familiaridade, ficar-se-á restrito à combinação "orgmode + pandoc".

**Atenção**: Os atalhos do teclado para os comandos emacs aqui
discutidos são àqueles do PCs, onde "C" significa a tecla "Ctrl" e
"M" a tecla "Alt". Para usuários de MAC, as devidas modificações
devem ser consideradas.

## Requisitos básicos

-   [Emacs](https://www.gnu.org/software/emacs/emacs.html).
-   [Orgmode](http://orgmode.org/) (nativo partir da versão 24.1 do emacs).
-   [Latex](http://www.latex-project.org/).
-   [Pandoc](http://pandoc.org/).

## Cabeçalho

No topo do arquivo .org sugeri-se que se coloque a linha: 

    #+STARTUP=latexpreview

Com isso, o usuário poderá observar em tempo real a fórmula tal
como aparecerá em sua versão de produção. Para tanto, bastar
digitar o atalho "C-c C-x C-l" quando o cursor estiver em cima da
expressão de interesse. Posteriormente, para retornar ao modo
edição, basta digitar "C-c C-c", novamente com o cursor sobre a
expressão.

## Convertendo de org => md

De posse do documento em seu formato .org, pode-se convertê-lo para o formado
.md ativando o comando "M-x org-md-exports-as-markdown". A conversão será feita
de imediato. Melhor ainda, deste ponto em diante, basta digitar o atalho
"C-c C-e m m" e uma nova versão do arquivo será automaticamente gerada. Alternativamente,
o usuário poderá digitar o atalho "C-c C-e m o" e o arquivo .md em sua nova versão também
será aberto.

## Avançado

Para uma experiência ainda mais dinâmica no desenvolvimento do trabalho, pode-se ainda utilizar
ferramentas adicionais, tais como as sugeridas abaixo:

-   [node.js](https://nodejs.org/)
-   [npm](http:www.npmjs.com)
-   [livedown](https://github.com/shime/livedown)
-   [emacs-livedown](https://github.com/shime/emacs-livedown)

Uma vez que essas ferramentas estejam devidamente instaladasm, o
usuário poderá abrir o arquivo .md e digitar "C-M-m". A partir daí,
as alterações do arquivo poderão ser acompanhas em tempo real no
browser da máquina de trabalho.

## Ainda mais avançado

Caso queira alçar voos ainda mais ousados, o usuário poderá se
utilizar de mais ferramentas, o que permitirá exportação do
documento original .org para formatos dos mais diversos - de fato,
para muito além daqueles permitidos pelo máquina de exportação do
próprio org-mode. Para tanto, o usuário deverá instalar em sua
máquina as seguintes ferramentas:

-   [pandoc](http://pandoc.org/%20)
-   [pandoc-mode](http://joostkremers.github.io/pandoc-mode/)

O programa pandoc é um verdadeiro canivete suíço, permitindo a
exportação de qualquer arquivo formato texto para outros formatos
de texto. Aqui, apenas arranha-se a superfície desse poderoso
*software*, e basta mencionar que esse *software* permite a
exportação de arquivos .org para formatos .tex, .md, .docx, entre
outros.

Como exemplo, o comando abaixo exporta o arquivo manual.org para
manual.md, no estilo *github*:

    pandoc -s manul.org -f org -t markdown_github -o manual.md

que pode ser digitado diretamente em um dos modos shell do emacs
(por exemplo, o eshell).  Reciprocamente, o arquivo .md pode ser
revertido para seu formato .org através do comando:

    pandoc -s manul.md -f mardown_github -t org -o manual.org

Como aqueles mais acostumados ao ambiente emacs ja devam
descofir, há de fato um modo do emacs para utilização do
pandoc. De fato, o uso do pandoc-mode permite que os comandos
acima sejam reproduzidos através do menu do modo. Entretanto, sua
utilização requer conhecimento do programa pandoc, e, portanto, a
maior motivação para sua utilização fica por conta do conforto de
utilizá-lo dentro do ambiente emacs sem a necessidade de digitar
longos comandos shell.
