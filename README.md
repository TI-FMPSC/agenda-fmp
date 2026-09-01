# Sistema Integrado FMP

Sistema web desenvolvido para integrar a gestão de espaços, salas de aula, laboratórios, estoque e registros administrativos da **Faculdade Municipal de Palhoça (FMP)**.

O sistema funciona diretamente no navegador e utiliza arquivos JSON armazenados no GitHub como base de dados.

---

## Funcionalidades

### Painel de Laboratórios e Espaços
- Visualização pública dos laboratórios, auditório e demais espaços.
- Identificação de espaços livres, agendados e em uso.
- Atualização automática.
- Navegação por data.
- Compatível com TV, computador, tablet e celular.

### Painel de Salas de Aula
- Visualização das salas utilizadas pelas turmas.
- Exibe:
  - sala;
  - curso e fase;
  - professor;
  - horário.
- Atualização automática por período.
- Identificação visual de alterações, mudanças para laboratório e conflitos.
- Grade organizada por:
  - ADS;
  - TPG;
  - Administração;
  - Pedagogia.

### Gestão das Salas
Área administrativa destinada à manutenção da grade de salas.

Permite:
- consultar a ocupação por data e horário;
- alterar a sala de uma turma;
- trocar o professor;
- realizar ajuste somente para uma data;
- alterar a grade semanal;
- remover ajustes pontuais;
- identificar conflitos de sala.

### Gestão dos Laboratórios
Permite administrar:
- Laboratório 01;
- Laboratório 02;
- Laboratório 03;
- Laboratório 04;
- Laboratório 05;
- Auditório;
- outros espaços institucionais.

Os agendamentos podem ser:
- únicos;
- semanais;
- em dias úteis;
- repetidos no mesmo dia da semana até o fim do mês.

Também é possível utilizar períodos completos, como:

- Matutino: `08:00 às 11:10`
- Vespertino: `13:00 às 17:00`
- Noturno: `18:50 às 22:00`

Além dos períodos parciais.

O mesmo professor pode possuir mais de um agendamento no mesmo dia e horário, desde que os espaços utilizados sejam diferentes.

### Professores
Os professores cadastrados na grade 2026/2 são apresentados automaticamente em ordem alfabética nos campos de seleção.

Também é possível informar manualmente outro responsável quando necessário.

### Gestão de Estoque
Módulo integrado para controle de materiais da FMP.

Permite:
- cadastro de materiais;
- consulta e busca de produtos;
- categorias;
- controle de quantidade;
- estoque mínimo;
- entradas e saídas;
- movimentações;
- relatórios;
- acompanhamento de materiais com estoque baixo.

A lista de **Materiais cadastrados** aparece no início da tela para facilitar a consulta.

### Usuários administrativos
O sistema possui autenticação administrativa.

Permite:
- criar usuários;
- editar usuários;
- alterar senha;
- remover usuários;
- controlar usuários ativos.

As senhas são armazenadas somente como hash.

A sessão administrativa possui duração de aproximadamente **30 minutos**.

Enquanto a sessão estiver válida, o usuário pode alternar entre os painéis públicos e a administração sem precisar realizar novo login.

### Logs de acesso
O sistema mantém um histórico das ações realizadas pelos usuários.

Exemplos:
- login;
- logout;
- criação de agendamento;
- alteração de agendamento;
- exclusão de agendamento;
- alterações na grade;
- alterações no estoque;
- criação e alteração de usuários;
- alterações de configuração.

A tela possui:
- busca por usuário ou ação;
- paginação;
- até 50 registros por página.

---

## Estrutura do repositório

```text
agenda-fmp/
├── index.html
└── dados/
    ├── agendamentos.json
    ├── grade-salas.json
    ├── usuarios.json
    ├── estoque.json
    └── log-acessos.json
```

---

## Arquivos JSON

### `dados/agendamentos.json`
Armazena os agendamentos de:

- laboratórios;
- auditório;
- espaços institucionais;
- alterações pontuais de salas.

### `dados/grade-salas.json`
Armazena:

- grade semestral;
- professores;
- cursos;
- fases;
- dias da semana;
- horários;
- salas-base das turmas.

### `dados/usuarios.json`
Armazena os usuários administrativos.

As senhas não são armazenadas em texto aberto.

### `dados/estoque.json`
Armazena:

- categorias;
- materiais;
- quantidades;
- estoque mínimo;
- fornecedores;
- locais;
- movimentações.

### `dados/log-acessos.json`
Armazena os registros das ações realizadas pelos usuários administrativos.

---

## Integração com GitHub

O sistema utiliza a **GitHub Contents API** para leitura e gravação dos arquivos JSON.

O token utilizado para gravação:

- fica armazenado somente no navegador;
- não deve ser colocado no `index.html`;
- não deve ser salvo em nenhum arquivo JSON;
- deve possuir permissão de leitura e escrita em `Contents`.

### Caminhos padrão

```text
dados/agendamentos.json
dados/grade-salas.json
dados/usuarios.json
dados/estoque.json
dados/log-acessos.json
```

---

## GitHub Pages

O sistema pode ser publicado utilizando o GitHub Pages.

Exemplo de endereço:

```text
https://SEU-USUARIO.github.io/agenda-fmp/
```

Após atualizar o `index.html` ou algum JSON, pode ser necessário aguardar alguns instantes para a publicação do GitHub Pages.

Se o navegador continuar exibindo uma versão antiga, utilize:

```text
Ctrl + F5
```

ou abra a página em uma janela anônima.

---

## Atualização do sistema

Para atualizar somente a interface ou funcionalidades:

1. substitua o arquivo `index.html`;
2. faça o commit no GitHub;
3. aguarde a atualização do GitHub Pages;
4. atualize o navegador.

Quando a alteração envolver algum banco de dados, substitua somente o JSON correspondente.

Evite substituir os JSONs sem necessidade, pois eles contêm os dados em uso pelo sistema.

---

## Segurança

Recomendações:

- não publicar tokens no repositório;
- utilizar token GitHub com acesso somente ao repositório necessário;
- limitar a permissão a `Contents: Read and write`;
- remover tokens antigos que não estejam mais em uso;
- manter as senhas dos usuários somente em hash;
- revisar periodicamente o arquivo de logs.

> **Observação:** se o repositório for público, os arquivos JSON também poderão ser acessados publicamente por meio do GitHub. Portanto, não armazene informações sigilosas nesses arquivos.

---

## Tecnologias utilizadas

- HTML5
- CSS3
- JavaScript
- JSON
- GitHub Pages
- GitHub Contents API
- LocalStorage / SessionStorage

O projeto não depende de servidor próprio ou banco de dados SQL.

---

## Cursos contemplados na grade

- Análise e Desenvolvimento de Sistemas — ADS
- Tecnologia em Processos Gerenciais — TPG
- Administração
- Pedagogia

---

## Instituição

**Faculdade Municipal de Palhoça — FMP**

Sistema desenvolvido para apoio à gestão interna de espaços, salas, laboratórios, estoque e rotinas administrativas da instituição.

---

## Status do projeto

Projeto em evolução contínua.

Melhorias e novos módulos podem ser incorporados mantendo a arquitetura baseada em:

```text
1 index.html + arquivos JSON
```

