# Módulo 01: Fundamentos da Computação

> **Trilha Do Zero ao Júnior — AWS Student Builder Group SENAI CIMATEC (2026.2)**  
> **Status:** 🟡 Em produção

Muitas pessoas iniciam na programação decorando comandos de uma linguagem sem compreender **onde** e **como** aquele código realmente ganha vida. O resultado costuma ser frustração ao lidar com erros de memória, lentidão, travamentos ou ao tentar colocar um sistema para rodar em um servidor real na nuvem.

Este módulo foi desenhado pensando na base sólida de um **Dev Júnior**: nosso objetivo não é formar engenheiros de hardware nem exigir que você decore circuitos eletrônicos, mas sim construir um **modelo mental claro** sobre como o computador funciona por baixo dos panos — desde os bits no processador e o papel da memória RAM até o funcionamento dos Sistemas Operacionais, a introdução ao ecossistema Linux e a diferença entre linguagens compiladas e interpretadas.

---

## 🎯 Objetivos de Aprendizagem

Ao final deste módulo, você será capaz de:
- Compreender **como um computador funciona**, como dados são representados em binário (bits e bytes) e o fluxo de Entrada, Processamento e Saída.
- Entender **como os processadores (CPU) funcionam**, incluindo o ciclo de execução de instruções (*Fetch-Decode-Execute*), *Clock*, núcleos (*Cores*), *Threads* e memória *Cache*.
- Explicar **como os programas rodam na memória**, diferenciando armazenamento persistente (SSD/HD) de memória volátil (RAM) e compreendendo a noção básica de *Stack* e *Heap*.
- Compreender o papel dos **Sistemas Operacionais (SO)** como intermediários entre o seu código e o hardware (gerenciamento de processos, memória e arquivos).
- Diferenciar na prática **linguagens compiladas, interpretadas e híbridas (JIT)**, entendendo como o código-fonte se transforma em instruções de máquina.
- Ter o primeiro contato com o ecossistema **Linux (Debian e Ubuntu)**, compreendendo por que ele domina o mercado de servidores e como estudá-lo de forma progressiva ao longo da carreira.

---

## 🗺️ Mapa de Conteúdos do Módulo

O conteúdo está organizado em três pilares fundamentais e progressivos:

```text
01-fundamentos/
├── README.md                               # Índice principal do módulo e guia de estudos
│
├── arquitetura-e-hardware/                 # O mundo físico: máquina, CPU e memória
│   ├── 01-como-funciona-um-computador.md
│   ├── 02-como-os-processadores-funcionam.md
│   └── 03-como-os-programas-rodam-na-memoria.md
│
├── sistemas-operacionais/                  # A camada de gestão: SO e ecossistema Linux
│   ├── 01-sistemas-operacionais.md
│   └── 02-introducao-ao-linux-ubuntu-e-debian.md
│
└── execucao-de-codigo/                     # Do código humano à execução na máquina
    ├── 01-codigo-fonte-e-codigo-de-maquina.md
    └── 02-linguagens-compiladas-e-interpretadas.md
```

---

## 🖥️ 1. Arquitetura e Hardware (`arquitetura-e-hardware/`)

Antes de uma linha de código executar qualquer lógica, ela depende de componentes físicos trabalhando em sincronia na casa dos bilionários de operações por segundo:

1. **[Como Funciona um Computador](arquitetura-e-hardware/01-como-funciona-um-computador.md)**: O sistema binário (por que computadores usam `0` e `1`), representação de textos e números (ASCII/Unicode), a Arquitetura de Von Neumann (Entrada, Processamento, Memória e Saída) e como a placa-mãe conecta os barramentos.
2. **[Como os Processadores Funcionam](arquitetura-e-hardware/02-como-os-processadores-funcionam.md)**: A anatomia da CPU (Unidade Lógica e Aritmética, Unidade de Controle e Registradores), o ciclo *Fetch-Decode-Execute*, frequência de *Clock* (GHz), diferença real entre *Cores* (núcleos físicos) e *Threads* (fluxos lógicos) e o papel da memória *Cache* (L1, L2, L3).
3. **[Como os Programas Rodam na Memória](arquitetura-e-hardware/03-como-os-programas-rodam-na-memoria.md)**: A hierarquia de memórias (velocidade vs. custo), a diferença entre Disco/SSD (persistente) e Memória RAM (volátil), o que acontece quando você dá "duplo clique" em um programa e uma visão descomplicada de endereçamento, **Stack** (pilha) e **Heap** (monte).

---

## 🐧 2. Sistemas Operacionais e Linux (`sistemas-operacionais/`)

Programadores raramente conversam direto com o hardware bruto; quem faz essa ponte com segurança e organização é o Sistema Operacional:

1. **[Sistemas Operacionais](sistemas-operacionais/01-sistemas-operacionais.md)**: O papel do SO como "maestro" da máquina, a separação entre *Kernel Space* (núcleo privilegiado) e *User Space* (onde rodam seus programas), gerenciamento de processos, concorrência/multitarefa, memória virtual e sistemas de arquivos.
2. **[Introdução ao Linux: Ubuntu, Debian e Guia de Longo Prazo](sistemas-operacionais/02-introducao-ao-linux-ubuntu-e-debian.md)**: O que é o Linux e o código aberto, por que a esmagadora maioria dos servidores web, contêineres Docker e instâncias na nuvem (AWS) rodam Linux, a relação entre as distribuições **Debian** e **Ubuntu**, primeiros comandos de sobrevivência no terminal e **como aprender Linux aos poucos ao longo da carreira** sem travar seus estudos atuais.

---

## ⚙️ 3. Execução de Código (`execucao-de-codigo/`)

O processador só entende sinais elétricos representados em binário. Como o código que escrevemos em português/inglês estruturado vira algo que a CPU consegue rodar?

1. **[Código-Fonte e Código de Máquina](execucao-de-codigo/01-codigo-fonte-e-codigo-de-maquina.md)**: A evolução das linguagens (código de máquina binário, Assembly e linguagens de alto nível), o conceito de abstração e o caminho entre um arquivo de texto e um processo em execução.
2. **[Diferença entre Linguagem Compilada e Interpretada](execucao-de-codigo/02-linguagens-compiladas-e-interpretadas.md)**: Como funcionam os **Compiladores** (ex: C, C++, Go, Rust) e os **Interpretadores** (ex: Python, JavaScript, Ruby), além das abordagens **Híbridas / Bytecode + JIT** (ex: Java, C#). Comparativo prático de performance, portabilidade, tempo de desenvolvimento e casos de uso no mercado.

---

## 🧭 Como Estudar Este Módulo

Para aproveitar este módulo sem se perder em detalhes excessivamente acadêmicos:
1. **Assista à base visual primeiro**: Comece assistindo à aula de Hardware do **CS50 de Harvard** indicada abaixo para visualizar como bits, CPU e memória RAM interagem.
2. **Siga a ordem do fluxo de um programa**:
   - Entenda a máquina física (**Como funciona um computador** e **Processadores**).
   - Veja onde seu código fica alojado (**Como os programas rodam na memória**).
   - Compreenda quem gerencia tudo isso (**Sistemas Operacionais**).
   - Descubra como seu código é traduzido para a máquina (**Linguagens Compiladas vs. Interpretadas**).
3. **Encare o Linux como uma maratona, não um sprint**: Leia o guia introdutório de **Linux (Ubuntu e Debian)** para entender os conceitos fundamentais, mas não sinta que precisa dominar administração de servidores agora — você ganhará fluência natural no terminal ao longo dos próximos módulos (Git, Redes, Backend e Docker).

---

## 📚 Materiais e Leituras Recomendadas

> [!TIP]
> **Dica de Ouro — Cursos e Certificados Gratuitos de Harvard (CS50):**  
> A **Universidade de Harvard** disponibiliza gratuitamente diversos cursos introdutórios e avançados da família **CS50** (*Computer Science 50*), ministrados pelo professor David J. Malan. Além de terem uma das melhores didáticas do mundo em computação, **os cursos do CS50 oferecem certificados gratuitos** (via plataforma oficial do CS50/OpenCourseWare ao concluir os projetos) que agregam enorme valor ao seu aprendizado e currículo! Vale muito a pena explorar o **[CS50T (Understanding Technology)](https://cs50.harvard.edu/technology/)**, o **[CS50x (Introduction to Computer Science)](https://cs50.harvard.edu/x/)** e o **[CS50P (Programming with Python)](https://cs50.harvard.edu/python/)**.

- 🎓 **Aula Base (Hardware, CPU, Memória e SO)**: [CS50's Understanding Technology — Week 1: Hardware](https://cs50.harvard.edu/technology/weeks/1/) — Aula essencial de Harvard cobrindo os 4 primeiros tópicos deste módulo de maneira visual e acessível.
- 📖 **Guia Prático (Compiladas vs. Interpretadas)**: [Diferenças entre Linguagens Interpretadas e Compiladas: Um Guia Prático para Iniciantes (CulturaDev)](https://culturadev.com.br/diferencas-entre-linguagens-interpretadas-e-compiladas-um-guia-pratico-para-iniciantes) — Leitura direta ao ponto sobre como o código é traduzido e executado.
- 🗺️ **Inspiração de Trilha**: Roadmap "Do Zero ao Júnior" por **Renato Augusto** (Arquiteto de Soluções) — Referência de mercado para os temas essenciais da base de computação.
- 🌐 **AWS SBG CIMATEC**: [Hub de Materiais Recomendados](https://awssbgcimateclanding.vercel.app/)

---

[⬅️ Voltar para o Roadmap Principal](../README.md)

