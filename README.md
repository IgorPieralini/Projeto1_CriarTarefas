# 🔨 Alterações Realizadas
# 1. Correção e Refatoração dos Métodos
Todos os métodos do projeto foram atualizados e refatorados para garantir um código mais limpo, eficiente e com melhores práticas de desenvolvimento. ✍️

# 2. Comentários no Código
O código foi amplamente comentado para fornecer explicações sobre as mudanças realizadas, permitindo que outros desenvolvedores compreendam facilmente a lógica implementada. 📝

# README - Correções no Código

## Introdução
Este documento explica as correções feitas no código original, destacando os problemas encontrados e as soluções aplicadas para melhorar a funcionalidade e a legibilidade.

---

## 1. Correção na Estrutura `ListaDeTarefas`
### Problema:
O código original declarava a estrutura como `ListaDeTarefa`, mas as funções estavam usando `ListaDeTarefas`, causando inconsistência.

### Solução:
O nome da struct foi padronizado para `ListaDeTarefas` para manter coerência.

---

## 2. Função `carregarTarefas`
### Problemas:
1. O parâmetro `char nome` deveria ser `const char *nome`, pois `nome` é uma string e não um caractere.
2. Falta de verificação do retorno da função `fread`.

### Solução:
- Alterado o tipo do parâmetro para `const char *nome`.
- Adicionada uma verificação para garantir que `fread` leu corretamente os dados.

```c
int carregarTarefas(ListaDeTarefas *lt, const char *nome) {
    FILE *fp = fopen(nome, "rb");
    if (fp == NULL) {
        return 1;
    }

    if (fread(lt, sizeof(ListaDeTarefas), 1, fp) != 1) {
        fclose(fp);
        return 1;
    }

    fclose(fp);
    return 0;
}
```

---

## 3. Função `salvarTarefas`
### Problemas:
1. Falta de ponto e vírgula (`;`) após `fopen(nome, "wb")`.
2. Não havia verificação se `fwrite` conseguiu salvar os dados corretamente.

### Solução:
- Corrigido o erro de sintaxe.
- Adicionada verificação para garantir que `fwrite` gravou os dados corretamente.

```c
int salvarTarefas(ListaDeTarefas *lt, const char *nome) {
    FILE *fp = fopen(nome, "wb");
    if (fp == NULL) {
        return 1;
    }

    if (fwrite(lt, sizeof(ListaDeTarefas), 1, fp) != 1) {
        fclose(fp);
        return 1;
    }

    fclose(fp);
    return 0;
}
```

---

## 4. Função `exibeMenu`
### Problemas:
1. O uso de `printf` para cada linha poderia ser otimizado.
2. A palavra "menu" deveria ter a primeira letra maiúscula.
3. "Listar tarefa" deveria ser "Listar tarefas" para manter concordância.

### Solução:
- Substituído `printf` por `puts`, que automaticamente adiciona `\n`.
- Corrigidos os textos para manter a consistência.

```c
void exibeMenu() {
    puts("Menu:");
    puts("1. Criar tarefa");
    puts("2. Deletar tarefa");
    puts("3. Listar tarefas");
    puts("0. Sair");
}
```

---

## Conclusão
As correções feitas melhoraram a segurança do código, corrigiram erros de sintaxe e tornaram a implementação mais consistente e legível.

# 👥 Membros do Projeto
Igor Marques Pieralini RA: 24224003-4
Victor Augusto Caramori André RA: 24.224.009-1

Isso organiza a estrutura de forma clara e prática. Se precisar de mais algum ajuste, estou à disposição!
