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

No início, baixamos o Nasm, o Fergo Raw e o Rufus 3.9. Em seguida, instalamos o Nasm, iniciamos o Rufus 3.9 e descompactamos o arquivo Zip do Fergo Raw. No entanto, ao tentar abrir o arquivo extraído, encontramos um problema: uma mensagem indicava que o componente "MSCOMCTL.OCX" ou uma de suas dependências não estava corretamente registrado. Embora tenha sido sugerido o uso de uma máquina virtual, ainda não conseguimos resolver esse problema. Procuraremos uma solução no futuro.

Após resolver esse problema, configuramos as variáveis de ambiente. Primeiro, obtivemos o diretório do Nasm, acessamos as propriedades do computador, buscamos as variáveis de ambiente, selecionamos a variável de sistema chamada "path" e adicionamos o diretório do Nasm. Após essa operação, verificamos no CMD que o Nasm agora é uma variável de ambiente e pode ser executado em qualquer lugar do computador.

Em seguida, organizamos os arquivos do nosso sistema operacional, criando uma pasta chamada "OSFiles" com duas subpastas: "FergoRaw" e "Rufus", que contêm as respectivas ferramentas mencionadas anteriormente.

Depois disso, abrimos o editor Notepad++ para criar um arquivo BAT, no qual executamos as instruções mostradas no vídeo. No final do segundo vídeo, o autor ensina como montar arquivos .ASM pelo Nasm.

No terceiro vídeo, aprendemos a baixar e instalar o Rufus 2.18 e a máquina virtual da Oracle. Em seguida, o autor demonstra como configurar o VirtualBox, criar uma máquina virtual e configurar o USB. Por fim, ele mostra como visualizar o número do pendrive no Windows e gerar o arquivo .vmdk que se conecta ao USB. O autor também revisa as configurações do VirtualBox.

### 2º Dia de Desenvolvimento

Como mencionado anteriormente, estávamos enfrentando dificuldades na abertura do arquivo extraído do Fergo Raw. Felizmente, um colega de turma trouxe uma solução para o problema.

Passos realizados:

1. O erro inicial (falta de registro do "MSCOMCTL.OCX") foi resolvido instalando uma biblioteca e ativando o "Controle ActiveX". Os arquivos necessários estão disponíveis em [link](https://drive.google.com/drive/folders/1Me89gAlCFmDR34rhr4ZKV8aXrGuqkbcI?usp=sharing). Em sistemas operacionais de 64 bits, foram utilizadas as seguintes linhas de comando no CMD: 

    ```
    cd C:\Windows\SysWOW64
    regsvr32 mscomctl.ocx
    ```

    Após a instalação da DLL, utilizamos o instalador ascentive-library.

2. Após resolver o primeiro erro, encontramos uma nova mensagem indicando que o componente "COMDLG32.OCX" estava ausente. Este problema foi resolvido de maneira semelhante ao anterior. Os arquivos necessários estão disponíveis em [link](https://drive.google.com/drive/folders/1gI9B59-HFAmwxaWLpeQTu-fW07-RxkaL?usp=sharing). Em sistemas operacionais de 64 bits, utilizamos as seguintes linhas de comando no CMD:

    ```
    cd C:\Windows\SysWOW64
    regsvr32 comdlg32.ocx
    ```

    *Obs: Para sistemas operacionais de 32 bits, utilize o caminho C:\Windows\System32.*

### 3º Dia de Desenvolvimento

Continuando a partir do que foi feito anteriormente, os passos seguintes são:

1. Instalar o Rufus, versão 2.18, disponível [aqui](https://rufus-portable.br.uptodown.com/windows/post-download/1678016).

2. Instalar o VirtualBox, versão 5.2.44, disponível [aqui](https://www.virtualbox.org/wiki/Download_Old_Builds_5_2), selecionando "Windows hosts".

3. Configurar a máquina virtual para reconhecer o pendrive. Utilize as seguintes linhas de comando no CMD:

    ```
    cd %programfiles%\oracle\virtualbox
    VBoxManage internalcommands createrawvmdk -filename "%USERPROFILE%"\.VirtualBox\usb.vmdk -rawdisk \\.\PhysicalDrive [numero]
    ```

    Substitua [numero] pelo número do disco.

4. Criar a máquina virtual com os dados desejados, selecionando "Utilizar um disco rígido virtual existente" e escolhendo o pendrive.

5. Criar um código inicial boot.asm utilizando o Notepad++, cujo código pode ser conferido nos diretórios deste repositório.

6. Abrir o FergoRaw, selecionar como output um arquivo de imagem chamado "System", escolher o código boot.bin e adicioná-lo à posição 1.

7. Utilizar o Rufus 2.18 para capturar a imagem "System" e colocá-la no pendrive, criando um disco bootável em "Imagem DD".

8. Para gerar o boot.bin, transformar boot.asm utilizando o Nasm. No CMD, execute:

    ```
    nasm -f bin boot.asm -o boot.bin
    ```

9. Retornar ao Oracle VM VirtualBox, iniciar a máquina virtual, criá-la e executá-la.

10. Aguardar a exibição dos métodos de "Hello World" na tela.

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
