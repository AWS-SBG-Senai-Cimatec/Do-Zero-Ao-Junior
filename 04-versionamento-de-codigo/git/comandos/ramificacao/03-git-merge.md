## 3. 🧩 `git-merge` — Mesclagem de Branches

Une o histórico de alterações de um branch secundário ao branch em que você está situado no momento.

<img width="860" height="292" alt="image" src="https://github.com/user-attachments/assets/6525b6ab-801c-4152-b035-b00b74229e3e" />

### 💻 Lista de Comandos Práticos

```bash
# Traz as alterações do 'branch-secundario' para o branch onde você está
git merge branch-secundario
```

* **Saída esperada:**
  ```text
  Updating a1b2c3d..e4f5g6h
  Fast-forward
   index.html | 2 +-
   1 file changed, 1 insertion(+), 1 deletion(-)
  ```
* **Entendendo a saída:**
  * `Updating a1b2c3d..e4f5g6h`: Indica a transição do commit inicial (`a1b2c3d`) para o commit final (`e4f5g6h`).
  * `Fast-forward`: O Git apenas moveu o ponteiro da branch atual para frente, pois não surgiram alterações concorrentes na branch principal durante o desenvolvimento.
  * `Resumo dos arquivos`: Exibe o número de arquivos alterados, linhas inseridas (`+`) e removidas (`-`).

---

```bash
# Força o registro de um ponto explícito de união no histórico (commit de merge para organização do histórico de alterações e merge)
git merge --no-ff branch-secundario
```

* **Saída esperada:**
  ```text
  Merge made by the 'ort' strategy.
   index.html | 2 +-
   1 file changed, 1 insertion(+), 1 deletion(-)
  ```
* **Entendendo a saída:**
  * `Merge made by the 'ort' strategy`: Informa a estratégia de mesclagem padrão do Git utilizada para criar um commit dedicado de união.
  * Ao contrário do *fast-forward*, esta opção gera um novo nó no histórico visual, garantindo rastreabilidade do encerramento da feature.

---

```bash
# Aborta uma mesclagem em andamento que gerou conflitos manuais (como mesmas linhas de código alteradas por pessoas diferentes e o git identificou)
git merge --abort
```

* **Saída esperada:**
  *(O terminal não retorna nenhuma mensagem de texto).*
* **Entendendo a saída:**
  * A ausência de texto indica sucesso imediato no Git (*silent success*). 
  * O repositório é restaurado ao estado exato anterior ao comando de merge com conflito, descartando qualquer marcador de conflito nos arquivos (`<<<<<<<`, `=======`, `>>>>>>>`).

---

### 🔍 Explicação Palavra a Palavra

* **`merge`**: Significa **fundir**, **mesclar** ou **unir**. Pega o histórico e combina com o branch ativo.
* **`--no-ff`** *(no fast-forward)*: Garante que o Git não apenas "avance o ponteiro", mas crie um commit de mesclagem visível no gráfico de histórico.
* **`--abort`**: Cancela a operação de mesclagem atual e restaura o código exatamente ao estado anterior à tentativa de junção.

> 📌 **Dica Prática para Iniciantes:**
> Sempre rode o comando `git status` antes de fazer um `switch` ou `merge` para ter certeza de que não deixou arquivos soltos e sem salvar no seu ambiente atual!
