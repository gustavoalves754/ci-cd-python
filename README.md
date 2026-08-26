# Pipeline CI/CD com Python e GitHub Actions

Atividade pratica da disciplina de Garantia de Software.

## Integrantes

- Gustavo Henrique de Oliveira Alves - RA: 4251920903
- Gustavo Michael Alves Pereira - RA: 4251920199

## Descricao

Neste projeto foi criada uma calculadora simples em Python com testes automatizados usando pytest. Tambem foi configurado um pipeline no GitHub Actions para executar os testes a cada push ou pull request na branch `main`.

O pipeline possui duas etapas principais: Continuous Integration e Continuous Delivery. A entrega so acontece quando os testes da etapa de integracao terminam com sucesso.

## Estrutura do projeto

```text
ci-cd-python/
├── .github/
│   └── workflows/
│       └── pipeline.yml
├── .gitignore
├── calculadora.py
├── test_calculadora.py
├── requirements.txt
└── README.md
```

## Execucao dos testes

Para instalar as dependencias e executar os testes localmente:

```bash
pip install -r requirements.txt
pytest -v
```

Foram criados testes para as operacoes de soma, subtracao, multiplicacao, divisao e tentativa de divisao por zero.

## Perguntas da atividade

### 1. O que representa a etapa de CI neste projeto?

A etapa de CI baixa o codigo do repositorio, configura o Python, instala as dependencias e executa os testes automaticamente. Assim, uma alteracao so pode seguir para a etapa de entrega se os testes forem aprovados.

### 2. O que impede a execucao do Continuous Delivery quando existe um defeito?

O job de `delivery` depende do job de `ci` por meio da configuracao `needs: ci`. Se algum teste falhar, o job de CI falha e o Continuous Delivery nao e executado.

### 3. Qual seria a proxima etapa necessaria para transformar este pipeline em Continuous Deployment?

Seria necessario adicionar uma etapa de deploy automatico depois dos testes, publicando a aplicacao diretamente em um ambiente de producao ou hospedagem sem depender de uma liberacao manual.
