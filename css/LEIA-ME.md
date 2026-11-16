# CSS organizado — Saúde para Todos

## Estrutura

```text
css/
├── base.css                 # estilos globais: variáveis, reset, layout, cabeçalho, rodapé e formulários
├── componentes.css          # componentes reutilizados nas páginas internas da plataforma
└── pages/
    ├── index.css
    ├── plataforma.css
    ├── localizacao.css
    ├── atendimento.css
    ├── inicial_profissional.css
    ├── profissional.css
    ├── login.css
    ├── cadastro.css
    ├── contato.css
    ├── privacidade.css
    └── termos.css
```

## Como instalar

Substitua a pasta CSS atual pela pasta `css` deste pacote (ou copie seu conteúdo para a pasta CSS existente). Os arquivos foram mantidos com seus nomes e regras originais para reduzir o risco de alterar a aparência ou quebrar seletores HTML.

## Links nos HTML

Use os caminhos abaixo, respeitando a ordem: base → componentes (quando indicado) → página.

| Página HTML | Folhas de estilo, nesta ordem |
|---|---|
| `index.html` | `../css/base.css` e `../css/pages/index.css` |
| `plataforma.html` | `../css/base.css`, `../css/componentes.css` e `../css/pages/plataforma.css` |
| `localizacao.html` | `../css/base.css`, `../css/componentes.css` e `../css/pages/localizacao.css` |
| `atendimento.html` | `../css/base.css`, `../css/componentes.css` e `../css/pages/atendimento.css` |
| `inicial_profissional.html` | `../css/base.css`, `../css/componentes.css` e `../css/pages/inicial_profissional.css` |
| `profissional.html` | `../css/base.css` e `../css/pages/profissional.css` |
| `login.html` / `login_profissional.html` | `../css/base.css` e `../css/pages/login.css` |
| `cadastro.html` / `cadastro_profissional.html` | `../css/base.css` e `../css/pages/cadastro.css` |
| `contato.html` | `../css/base.css` e `../css/pages/contato.css` |
| `privacidade.html` | `../css/base.css` e `../css/pages/privacidade.css` |
| `termos.html` | `../css/base.css` e `../css/pages/termos.css` |

> Os caminhos `../css/` pressupõem que os HTML estejam em uma pasta irmã de `css`. Se os HTML estiverem na raiz do projeto, retire o `../`.

### Exemplo de `<head>` para página interna

```html
<link rel="stylesheet" href="../css/base.css">
<link rel="stylesheet" href="../css/componentes.css">
<link rel="stylesheet" href="../css/pages/plataforma.css">
```

### Exemplo para a página inicial

```html
<link rel="stylesheet" href="../css/base.css">
<link rel="stylesheet" href="../css/pages/index.css">
```

## Decisões e cuidados

1. `base.css` permanece como fundação global. Não o carregue depois do CSS específico da página, pois isso pode sobrescrever regras locais.
2. `componentes.css` deve ser carregado somente nas páginas que usam os componentes compartilhados descritos no cabeçalho do arquivo. Isso evita aplicar estilos extras sem necessidade.
3. Os arquivos `login.css`, `cadastro.css`, `privacidade.css` e `termos.css` são atualmente placeholders ou quase vazios. Foram mantidos para preservar os links existentes e permitir estilos específicos no futuro. Podem ser removidos do HTML se não forem necessários.
4. Não renomeei classes duplicadas como `.step`, `.filters`, `.eyebrow` e `.section-head`: a alteração exigiria revisar também os HTML. Se páginas diferentes carregam seus CSS separadamente, a duplicidade pode não causar conflito visual, mas vale planejar nomes mais específicos antes de consolidar esses estilos.
5. As animações foram mantidas nos arquivos de origem para evitar duplicar/remover `@keyframes` sem validar todos os usos.
6. Após atualizar os caminhos, teste cada página em desktop e celular. Confirme especialmente filtros CSS com `:has()`, formulários, navegação e estados `:target`.

## Importante

Este pacote reorganiza os arquivos e seus caminhos, mas não altera deliberadamente o conteúdo das regras CSS. Como os HTML não foram incluídos nesta etapa, os caminhos devem ser ajustados conforme a localização real deles no projeto.
