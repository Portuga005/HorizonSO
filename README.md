# HorizonSO: Desbravando o Horizonte dos Sistemas Operacionais

Ferramentas Utilizadas:

O sistema é projetado para ser executado a partir de um pendrive ou diskette, podendo ser utilizado em máquinas reais ou virtuais.
As principais ferramentas incluem o NASM para manipulação em Assembly, o Fergo Raw para criação de arquivos de imagem e o Rufus 3.9 para preparação do pendrive ou diskette.

# Links para as ferramentas:

NASM: https://www.nasm.us/pub/nasm/releasebuilds/2.14.03rc2/win64/
<br> Fergo Raw: https://www.fergonez.net/softwares/fraw <br/>
Rufus: https://rufus.ie/downloads/ 
<br>Além disso, será utilizado o editor Notepad++ para facilitar o desenvolvimento.<br/>

Em um desafio acadêmico instigante, nasceu o HorizonSO. Este projeto, forjado nos corredores da faculdade, visa criar um Sistema Operacional Básico, utilizando a linguagem Assembly. Munidos da matéria de Sistemas Operacionais e uma playlist de vídeos instrutivos, embarcamos em uma jornada rumo ao desconhecido, alimentados por curiosidade e determinação.

Contudo, como toda grande aventura, nossos primeiros passos foram marcados por obstáculos. O encontro com erros como o famigerado MSCOMCTL.OCX nos fez enfrentar desafios iniciais. Porém, não nos intimidamos. Com resiliência e uma busca incansável por soluções, encontra-se a luz no fim do túnel. Graças a um comando simples, mas crucial, executado com a bomba de administradores, logramos superar tais adversidades:

cd C:\Windows\SysWOW64 regsvr32 mscomctl.ocx

E quando o COMDLG32.OCX estava próximo do seu rosto, pronto para encará-lo de frente. Mais um desafio, mais uma vitória: regsvr32 C:\Windows\SysWOW64\comdlg32.ocx

Porém, aprender uma lição valiosa: a importância de se contar com uma boa companhia. Recomendamos o uso de uma máquina virtual como refúgio seguro para nossas experimentações. Com ferramentas como VirtualBox e NASM em mãos, trilhamos o caminho rumo à concretização de nosso projeto.

Seguindo os passos delineados nos vídeos da playlist selecionada com cuidado, compreendemos a necessidade de um pendrive como ponte entre o nosso sistema embrionário e a máquina virtual que o acolherá. A configuração detalhada da VM, um ritual meticuloso, complementa nosso processo de desenvolvimento.

HorizonSO não é apenas um projeto, é uma jornada de descobertas, de aprendizado e superação. Nele, não encontramos apenas os desafios técnicos, mas também o valor da persistência e da colaboração. Rumo ao horizonte dos sistemas operacionais, marchamos, certos e confiantes, prontos para enfrentar o que quer que o futuro nos reserve.
