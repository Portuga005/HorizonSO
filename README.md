# HorizonSO: Desbravando o Horizonte dos Sistemas Operacionais

## Visão Geral

O HorizonSO é um projeto destinado a criar um Sistema Operacional Básico utilizando a linguagem Assembly. Nasceu de um desafio acadêmico e floresceu nos corredores da faculdade, impulsionado pela curiosidade e determinação de seus idealizadores. Este README oferece uma visão geral do projeto, destacando as ferramentas utilizadas, os desafios enfrentados e as lições aprendidas ao longo do caminho.

## Ferramentas Utilizadas

O projeto é desenvolvido com uma combinação cuidadosa de ferramentas essenciais para a construção de um Sistema Operacional. Aqui estão as principais ferramentas utilizadas:

- **NASM:** O NASM é utilizado para manipulação em Assembly, uma linguagem fundamental para o desenvolvimento de sistemas operacionais.
  - [Download NASM](https://www.nasm.us/pub/nasm/releasebuilds/2.14.03rc2/win64/)

- **Fergo Raw:** Esta ferramenta é empregada na criação de arquivos de imagem, uma parte crucial do processo de desenvolvimento.
  - [Download Fergo Raw](https://www.fergonez.net/softwares/fraw)

- **Rufus 3.9:** O Rufus é utilizado para preparar o pendrive ou diskette a partir do qual o sistema será executado, seja em máquinas reais ou virtuais.
  - [Download Rufus](https://rufus.ie/downloads/)

- **Notepad++:** Para facilitar o desenvolvimento, o editor Notepad++ é recomendado.

## Desenvolvimento

### 1º Dia de Desenvolvimento

Inicialmente, seguimos os passos para preparar nosso ambiente de desenvolvimento. Baixamos e instalamos o Nasm, o Fergo Raw e o Rufus 3.9. Após a instalação do Nasm, tentamos abrir o arquivo extraído do Fergo Raw, mas nos deparamos com um problema relacionado ao componente "MSCOMCTL.OCX". Embora tenhamos tentado resolver esse problema usando uma máquina virtual, os autores do repositório ainda não encontraram uma solução definitiva. Continuaremos buscando uma solução para isso no futuro.

Após lidar com esse contratempo, avançamos para a configuração das variáveis de ambiente. Adicionamos o diretório do Nasm às variáveis de sistema para que ele possa ser acessado de qualquer lugar no computador. Feito isso, organizamos os arquivos do nosso sistema operacional em uma pasta chamada "OSFiles", que contém subpastas para o Fergo Raw e o Rufus, cada uma com suas respectivas ferramentas.

Em seguida, abrimos o Notepad++ para criar um arquivo de lote (BAT) e seguir as instruções do vídeo. Finalmente, aprendemos como montar arquivos .ASM usando o Nasm.

### 2º Dia de Desenvolvimento

Enfrentamos problemas adicionais ao tentar abrir o arquivo extraído do Fergo Raw. Felizmente, um colega de turma compartilhou uma solução conosco. Primeiro, resolvemos o erro inicial relacionado ao "MSCOMCTL.OCX" instalando uma biblioteca e ativando um "Controle ActiveX". Esses passos foram detalhados em tutoriais disponíveis online. Após isso, encontramos outro erro referente ao componente "COMDLG32.OCX", que também foi resolvido seguindo instruções semelhantes.

### 3º Dia de Desenvolvimento

Avançamos na instalação do Rufus 2.18 e da VirtualBox 5.2.44. Aprendemos a configurar a VirtualBox para reconhecer nosso pendrive, usando comandos no prompt de comando. Criamos uma máquina virtual, escrevemos um código inicial em assembly usando o Notepad++, e utilizamos o FergoRaw para criar uma imagem de sistema. Em seguida, usamos o Rufus para criar um disco inicializável no pendrive. Por fim, executamos a máquina virtual no Oracle VM VirtualBox e vimos os resultados na tela.

## Utilizando o Fergo Raw

Para colocar os arquivos nos setores especificados utilizando o Fergo Raw, siga estas instruções:

1. Abra o Fergo Raw.
2. Carregue o arquivo de imagem que deseja modificar.
3. Para colocar o arquivo `bootloader.bin` no setor 1, navegue até a aba "Setores" e selecione o setor desejado. Em seguida, clique em "Escrever Arquivo" e selecione o arquivo `bootloader.bin`.
4. Repita o processo para os arquivos `kernel.bin` e `window.bin`, colocando-os nos setores 2 e 4, respectivamente.
5. Após colocar todos os arquivos nos setores corretos, salve a imagem resultante.
   exemplo:
    ![Captura de tela 2024-05-07 114033](https://github.com/Portuga005/HorizonSO/assets/49793708/d1b88176-19ba-4c0e-b9b8-ed87c27db32d)

## Conclusão

O HorizonSO não é apenas um projeto; é uma jornada de descobertas, aprendizado e superação. Nele, encontramos não apenas desafios técnicos, mas também o valor da persistência e colaboração. Rumo ao horizonte dos sistemas operacionais, marchamos, certos e confiantes, prontos para enfrentar o que quer que o futuro nos reserve.
