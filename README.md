# Boas vindas ao repositório do projeto TING (Trybe is not Google)!

Projeto desenvolvido como requisito parcial para conclusão do módulo de Ciência da Computação do curso de Desenvolvimento Web da Trybe. Este projeto, desenvolvido em **Python**, tem como objetivo implementar uma aplicação que simule um algoritmo de indexação de documentos, algo similar ao do Google. Ou seja, um programa que permita anexar arquivos de texto e posteriormente opere funções de busca sobre tais arquivos.

> Com a quantidade de informações disponíveis na Web, encontrar o que você precisa seria quase impossível sem nenhuma ajuda para classificá-las. Os sistemas de classificação do Google organizam centenas de bilhões de páginas da Web, no índice da pesquisa, para fornecer os resultados mais úteis e relevantes em uma fração de segundo. Além disso tudo, a Google também precisa se preocupar em apresentar os resultados de uma maneira que ajude você a encontrar o que está procurando com mais facilidade ainda.

#### Analisar palavras

> Compreender o significado da sua pesquisa é crucial para retornarmos boas respostas. Por isso, para encontrar páginas com informações relevantes, o primeiro passo do projeto é analisar o significado das palavras na consulta de pesquisa. Desenvolvemos modelos linguísticos para decifrar as sequências de palavras que precisamos procurar no índice.

Cabe destacar que, neste projeto, não me apeguei à análise de significados ou busca por sinônimos. O objetivo foi tão só identificar ocorrências de termos em arquivos _TXT_. Neste contexto, buscou-se implementar uma aplicação que permite anexar arquivos de texto e posteriormente operar funções de busca sobre tais arquivos.

Sendo assim, esta aplicação possui dois módulos:

- gerenciamento de arquivos

- buscas

---


# Sumário

- [Habilidades](#habilidades)
- [Desenvolvimento](#desenvolvimento)
- [Data de Entrega](#data-de-entrega)
  
`Requisitos obrigatórios:`
    - [1 - Implemente uma fila para armazenar os arquivos que serão lidos](#1---implemente-uma-fila-para-armazenar-os-arquivos-que-serão-lidos)
    - [2 - Implemente uma função `txt_importer` dentro do módulo `file_management` capaz de importar notícias a partir de um arquivo TXT, utilizando "\n" como separador. Todas as mensagens de erro devem ir para a `stderr`](#2---implemente-uma-função-txt_importer-dentro-do-módulo-file_management-capaz-de-importar-notícias-a-partir-de-um-arquivo-txt-utilizando-n-como-separador-todas-as-mensagens-de-erro-devem-ir-para-a-stderr)
    - [3 - Implemente uma função `process` dentro do módulo `file_process` capaz de ler o arquivo carregado na função anterior e efetuar o preprocessamento do conteúdo](#3---implemente-uma-função-process-dentro-do-módulo-file_process-capaz-de-ler-o-arquivo-carregado-na-função-anterior-e-efetuar-o-preprocessamento-do-conteúdo)
    - [4 - Implemente uma função `remove` dentro do módulo `file_process` capaz de remover o primeiro arquivo processado](#4---implemente-uma-função-remove-dentro-do-módulo-file_process-capaz-de-remover-o-primeiro-arquivo-processado)
    - [5 - Implemente uma função `file_metadata` dentro do módulo `file_process` capaz de apresentar as informações superficiais dos arquivos processados](#5---implemente-uma-função-file_metadata-dentro-do-módulo-file_process-capaz-de-apresentar-as-informações-superficiais-dos-arquivos-processados)
    - [6 - Implemente uma função `exists_word` dentro do módulo `word_search`, que valide a existência da palavra em todos os arquivos processados. Para cada palavra encontrada, deve-se listar sua linha conforme apresentação abaixo](#6---implemente-uma-função-exists_word-dentro-do-módulo-word_search-que-valide-a-existência-da-palavra-em-todos-os-arquivos-processados-para-cada-palavra-encontrada-deve-se-listar-sua-linha-conforme-apresentação-abaixo)
    - [7 - Implemente uma função `search_by_word` dentro do módulo `word_search`, que busque a palavra em todos os arquivos processados. Para cada palavra encontrada, deve-se listar sua linha, o conteúdo e o arquivo da ocorrência](#7---implemente-uma-função-search_by_word-dentro-do-módulo-word_search-que-busque-a-palavra-em-todos-os-arquivos-processados-para-cada-palavra-encontrada-deve-se-listar-sua-linha-o-conteúdo-e-o-arquivo-da-ocorrência)


---

# Habilidades

- Manipular Pilhas

- Manipular Deque

- Manipular Nó & Listas ligadas

- Manipular Listas duplamentes ligadas

--- 

## Desenvolvimento

Este repositório já contém um _template_ com a estrutura de diretórios e arquivos, tanto de código quanto de teste criados. Veja abaixo:

```md
.
├── statics
│   ├── arquivo_teste.txt
│   ├── novo_paradigma_globalizado.txt
│   └── novo_paradigma_globalizado-min.txt
├── tests
├── ting_file_management
│   ├── file_management.py
│   └── file_process.py
├── ting_word_searches
│   └── word_search.py
├── README.md
├── requirements.txt
└── setup.cfg
```

Apesar do projeto já possuir uma estrutura base, eu implementei as funções, conforme os requisitos técnicos descritos a seguir. 

A criação do ambiente virtual e instalação das dependências do projeto é feita ao rodar os scripts abaixo na raiz do projeto:

```bash
$ python3 -m venv .venv

$ source .venv/bin/activate

$ python3 -m pip install -r dev-requirements.txt
```

O arquivo `requirements.txt` contém todos as dependências que são utilizadas no projeto. 

---

## Data de Entrega

  - Foram `2` dias de projeto.
  - Data de entrega para avaliação final do projeto: `11/02/2022 - 14:00h`.

---

## Requisitos obrigatórios:

### Pacote `ting_file_management`

#### 1 - Implemente uma fila para armazenar os arquivos que serão lidos.

Preencha a classe `Queue`, presente no arquivo `queue.py` utilizando as estruturas vistas no módulo.

A fila (Queue) deve ser uma estrutura `FIFO`, ou seja, o primeiro item a entrar, deve ser o primeiro a sair. Utilize seus conhecimentos de estruturas de dados para otimizar as operações implementadas.

Devemos implementar os métodos de inserção (`enqueue`), remoção (`dequeue`) e busca (`search`).

Vamos expor o tamanho da nossa fila através do método `__len__`.

Na busca, caso um índice inválido seja passado, uma exceção do tipo `IndexError` deve ser lançada. Para uma fila com `N` elementos, índices válidos são inteiros entre `0` e `N-1`.

##### As seguintes verificações serão feitas:

- 1.1 - Será validado que o método `enqueue` deve adicionar um valor a fila, modificando seu tamanho.

- 1.2 - Será validado que o método `dequeue` deve remover o elemento a mais tempo na fila, modificando seu tamanho.

- 1.3 - Será validado que o método `search` deve retornar um valor da fila à partir de um índice válido.

- 1.4 - Será validado que o método `search` deve lançar a exceção `IndexError` quando o índice for inválido.

#### 2 - Implemente uma função `txt_importer` dentro do módulo `file_management` capaz de importar notícias a partir de um arquivo TXT, utilizando "\n" como separador. Todas as mensagens de erro devem ir para a `stderr`.

**Exemplo simples de um arquivo txt a ser importado:**

```md
Acima de tudo,
é fundamental ressaltar que a adoção de políticas descentralizadoras nos obriga
à análise do levantamento das variáveis envolvidas.
```

- Caso o arquivo TXT não exista, deve ser exibida a mensagem: "Arquivo {path_file} não encontrado";

- Caso a extensão do arquivo seja diferente de .txt, deve ser exibida uma mensagem: "Formato inválido" na `stderr`;

- A função deve retornar uma lista contendo as linhas do arquivo.

##### As seguintes verificações serão feitas:

- 2.1 - Será validado que ao executar o método `txt_importer` deve retornar uma lista contendo as linhas do arquivo;

- 2.2 - Será validado que ao executar o método `txt_importer` com um arquivo TXT que não exista, deve ser exibida a mensagem: `Arquivo {path_file} não encontrado` na `stderr`;

- 2.3 - Será validado que ao executar o método `txt_importer` com uma extensão diferente de `.txt`, deve ser exibida uma mensagem: `Formato inválido` na `stderr`.

#### 3 - Implemente uma função `process` dentro do módulo `file_process` capaz de ler o arquivo carregado na função anterior e efetuar o preprocessamento do conteúdo.

**Exemplo de retorno**:

```python
{
    "nome_do_arquivo": "arquivo_teste.txt", # Nome do arquivo recém adicionado
    "qtd_linhas": 3,                        # Quantidade de linhas existentes no arquivo
    "linhas_do_arquivo": [...]              # linhas retornadas pela função do requisito 2
}
```

- A função irá receber como parâmetro a fila que implementamos no requisito 1 e o caminho do arquivo.

- Por padrão deve-se ignorar arquivos com o mesmo nome;

- Não deve haver limites de linhas a serem analisadas;

- O exemplo de saída acima deve ser emitido após cada nova inserção válida, via `stdout`;

- O conteúdo processado deve ser adicionado a uma fila.

##### As seguintes verificações serão feitas:

- 3.1 - Será validado que ao executar a função `process` com o mesmo nome a execução deverá ser ignorada;

- 3.2 - Será validado que ao executar a função `process` com sucesso deverá retornar mensagem via `stdout`.

#### 4 - Implemente uma função `remove` dentro do módulo `file_process` capaz de remover o primeiro arquivo processado

- A função irá receber como parâmetro a fila que implementamos no requisito 1.

- Por padrão deve-se ignorar a operação caso não hajam arquivos e emitir a mensagem `Não há elementos`;

- Em caso de sucesso de remoção, deve ser emitido a mensagem: "`Arquivo {path_file} removido com sucesso`".

##### As seguintes verificações serão feitas:

- 4.1 - Será validado que ao executar a função `remove` com sucesso deverá exibir mensagem correta via `stdout`.

- 4.2 - Será validado que ao executar a função `remove` um arquivo inexistente deverá exibir a mensagem correta via `stdout`.

#### 5 - Implemente uma função `file_metadata` dentro do módulo `file_process` capaz de apresentar as informações superficiais de um arquivo processado.

- Baseado na posição informada, deve ser apresentado as informações relacionadas ao arquivo, parecido com o apresentado abaixo;

- Em caso da posição não existir, deve ser exibida uma mensagem de erro: "`Posição inválida`" na `stderr`.

- A função irá receber como parâmetro a fila que implementamos no requisito 1 e o índice a ser buscado.

**Exemplo de mensagem com sucesso**:

```python
{
    "nome_do_arquivo": "arquivo_teste.txt",
    "qtd_linhas": 3,
    "linhas_do_arquivo": [...]
}
```

##### As seguintes verificações serão feitas:

- 5.1 - Será validado que ao executar a função `file_metadata` com sucesso deverá exibir a mensagem correta via `stdout`.

- 5.2 - Será validado que ao executar a função `file_metadata` com posição inválida deverá exibir a mensagem correta via `stderr`.

### Pacote `ting_word_searches`

#### 6 - Implemente uma função `exists_word` dentro do módulo `word_search`, que valide a existência da palavra em todos os arquivos processados. Para cada palavra encontrada, deve-se listar sua linha conforme apresentação abaixo.

- A busca deve ser _case insensitive_ e deve retornar uma lista no formato:

```json
[{
  "palavra": "de",
  "arquivo": "arquivo_teste.txt",
  "ocorrencias": [
    {
      "linha": 1
    },
    {
      "linha": 2
    }
  ]
}]
```

- Caso a palavra não seja encontrada em nenhum arquivo, deve-se retornar uma lista vazia.

##### As seguintes verificações serão feitas:

- 6.1 - Será validado que ao executar a função `exists_word` com sucesso deverá retornar a mensagem correta.

- 6.2 - Será validado que ao executar a função `exists_word` com palavra inexistente deverá retornar uma lista vazia.

#### 7 - Implemente uma função `search_by_word` dentro do módulo `word_search`, que busque a palavra em todos os arquivos processados. Para cada palavra encontrada, deve-se listar sua linha, o conteúdo e o arquivo da ocorrência.

- A busca deve ser _case insensitive_ e deve retornar uma lista no formato:

```json
[{
  "palavra": "de",
  "arquivo": "arquivo_teste.txt",
  "ocorrencias": [
    {
      "linha": 1,
      "conteudo": "Acima de tudo,"
    },
    {
      "linha": 2,
      "conteudo": "é fundamental ressaltar que a adoção de políticas descentralizadoras nos obriga"
    }
  ]
}]
```

- Caso a palavra não seja encontrada em nenhum arquivo, deve-se retornar uma lista vazia.

##### As seguintes verificações serão feitas:

- 7.1 - Será validado que ao executar a função `search_by_word` com sucesso deverá retornar a mensagem.

- 7.2 - Será validado que ao executar a função `search_by_word` com palavra inexistente deverá retornar uma lista vazia.

---

### DURANTE O DESENVOLVIMENTO

- Faça `commits` das alterações que você fizer no código regularmente

- Lembre-se de sempre após um (ou alguns) `commits` atualizar o repositório remoto

- Os comandos que você utilizará com mais frequência são:
  1. `git status` _(para verificar o que está em vermelho - fora do stage - e o que está em verde - no stage)_
  2. `git add` _(para adicionar arquivos ao stage do Git)_
  3. `git commit` _(para criar um commit com os arquivos que estão no stage do Git)_
  4. `git push -u nome-da-branch` _(para enviar o commit para o repositório remoto na primeira vez que fizer o `push` de uma nova branch)_
  5. `git push` _(para enviar o commit para o repositório remoto após o passo anterior)_

---

### DEPOIS DE TERMINAR O DESENVOLVIMENTO (OPCIONAL)

Para sinalizar que o seu projeto está pronto para o _"Code Review"_ dos seus colegas, faça o seguinte:

- Vá até a página **DO SEU** _Pull Request_, adicione a label de _"code-review"_ e marque seus colegas:

  - No menu à direita, clique no _link_ **"Labels"** e escolha a _label_ **code-review**;

  - No menu à direita, clique no _link_ **"Assignees"** e escolha **o seu usuário**;

  - No menu à direita, clique no _link_ **"Reviewers"** e digite `students`, selecione o time `tryber/students-sd-010-a`.

Caso tenha alguma dúvida, [aqui tem um video explicativo](https://vimeo.com/362189205).

---

### REVISANDO UM PULL REQUEST

Use o conteúdo sobre [Code Review](https://app.betrybe.com/course/real-life-engineer/code-review) para te ajudar a revisar os _Pull Requests_.

#VQV 🚀
