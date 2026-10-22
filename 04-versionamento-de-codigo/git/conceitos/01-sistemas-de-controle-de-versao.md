# 01. `Sistemas de Controle de Versão`

## 📖 Visão Geral

Um **Sistema de Controle de Versão** (VCS — *Version Control System*) é uma ferramenta responsável por gerenciar e registrar todas as alterações feitas em arquivos e códigos-fonte ao longo do tempo. Ele funciona como uma "máquina do tempo" para o projeto, permitindo recuperar versões antigas, acompanhar quem fez cada modificação e integrar o trabalho de múltiplos desenvolvedores de forma organizada.

Sem um VCS, o desenvolvimento de software torna-se caótico e suscetível a perdas graves de dados.

---

## 🛑 O Problema do Versionamento Manual

Antes dos sistemas automatizados, o controle de arquivos era feito manualmente por meio de cópias locais e pastas zipadas. Essa abordagem traz sérios riscos para projetos de qualquer porte:

* **Poluição e Confusão:** Pastas com nomes como `projeto_v1`, `projeto_final`, `projeto_final_v2` e `projeto_agora_vai_final`.
* **Perda de Código:** Sobrescrita acidental de alterações quando dois desenvolvedores editam o mesmo arquivo simultaneamente.
* **Falta de Rastreabilidade:** Impossibilidade de saber *quem* alterou determinada linha, *quando* a alteração foi feita e *por qual motivo*.
* **Recuperação Complexa:** Dificuldade em reverter um bug específico sem desfazer outras funcionalidades criadas no mesmo período.

---

## 📜 Evolução Histórica dos VCS

Os sistemas de controle de versão evoluíram em três gerações principais:

### 1. Sistemas Locais (Ex: RCS)
* **Como funcionavam:** Mantinham um banco de dados simples no próprio computador do usuário para registrar as diferenças (*patches*) dos arquivos.
* **Limitação:** Funciona apenas localmente. Não permite a colaboração remota em equipe.

### 2. Sistemas Centralizados (Ex: SVN, CVS)
* **Como funcionavam:** Utilizam um único servidor central que armazena todo o histórico do projeto. Os desenvolvedores baixam os arquivos (*checkout*), fazem alterações e enviam de volta (*commit*).
* **Limitação:** Ponto único de falha (*Single Point of Failure*). Se o servidor central ficar offline ou o disco corromper, ninguém consegue trabalhar ou consultar o histórico.

### 3. Sistemas Distribuídos (Ex: Git, Mercurial)
* **Como funcionam:** Cada desenvolvedor possui uma cópia completa do repositório em sua máquina local, incluindo todo o histórico de alterações e ramificações (*branches*).
* **Vantagem:** Total independência do servidor central para o trabalho diário.

| Modelo | Armazenamento do Histórico | Dependência da Rede | Ponto Único de Falha |
| :--- | :--- | :--- | :--- |
| **Local** | Apenas na máquina local | 🟢 Nenhuma | 🟡 Alto (falha no disco local) |
| **Centralizado** | Apenas no servidor central | 🔴 Alta (exige conexão constante) | 🔴 Altíssimo (falha no servidor) |
| **Distribuído (Git)** | Servidor e todas as máquinas | 🟡 Baixa (apenas no push/pull) | 🟢 Nulo (múltiplas cópias completas) |

---

## ⚡ Benefícios Essenciais do Modelo Distribuído

O Git adota o modelo distribuído e oferece vantagens cruciais para a engenharia de software moderna:

1. **Trabalho Offline:** Commits, consultas de histórico, criação e fusão de *branches* são executados localmente e sem necessidade de conexão com a internet.
2. **Integridade de Dados:** Cada alteração é identificada por uma chave criptográfica única (hash SHA), garantindo que o código não seja alterado ou corrompido sem detecção.
3. **Agilidade e Desempenho:** A maioria das operações lê e escreve diretamente no disco local, tornando o processo extremamente rápido.
4. **Histórico Completo Local:** Todo o histórico de commits do projeto está disponível instantaneamente para inspeção local.

---

## 🔗 Próximos Passos

>Para entender como o Git gerencia esses arquivos e garante a integridade dos dados na prática, acesse o próximo guia:

* [02. Como o Git Funciona por Baixo dos Panos](02-como-o-git-funciona-por-baixo-dos-panos.md)
---