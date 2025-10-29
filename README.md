# Site Institucional - ONG Vidas (Projeto de Estudo)

[![Autor](https://img.shields.io/badge/Feito%20por-Íris%20Hanielle-blue)](https://github.com/irisrezende)

Este repositório contém o código-fonte do site institucional da "ONG Vidas", um projeto focado na aplicação de especificações técnicas obrigatórias de nível profissional.

O objetivo principal foi evoluir um site HTML/Tailwind básico, que usava o CDN de desenvolvimento, para um projeto pronto para produção, implementando as melhores práticas de **Controle de Versão (GitFlow)**, **Acessibilidade Universal (WCAG AA)** e **Otimização de Performance**.

## 🚀 O que foi feito: Evolução e Estrutura

O desafio era pegar um projeto funcional e aplicar uma camada completa de profissionalização. Para organizar o código e facilitar futuras manutenções, eu reestruturei o projeto.

Originalmente, o site usava um único arquivo `index.html` com o script do Tailwind CDN, o que é ótimo para desenvolver, mas péssimo para a performance do usuário.

Eu criei uma **nova estrutura de arquivos e pastas** para separar as responsabilidades e otimizar os recursos:

 `/css/input.css`: Este arquivo agora contém apenas as diretivas `@tailwind` (base, components, utilities).
 `/css/style.css`: **(Novo arquivo gerado)** Este é o arquivo de CSS final e minificado. O Tailwind faz uma varredura nos meus arquivos HTML e gera um `style.css` minúsculo, contendo *apenas* as classes que eu realmente usei no projeto.
 `/js/app.js`: O código JavaScript do menu mobile, que antes estava solto no HTML, foi movido para cá.
 `/js/app.min.js`: **(Novo arquivo gerado)** A versão minificada do `app.js`, que é a que o `index.html` realmente carrega.
 `tailwind.config.js`: **(Novo arquivo)** O coração da otimização. É aqui que eu configuro o Tailwind, habilito o Modo Escuro e digo a ele quais arquivos monitorar.

Essa nova estrutura torna o `index.html` muito mais limpo e leve, e permite que qualquer alteração de estilo ou script seja feita em seus respectivos arquivos, facilitando o acesso e a comparação de código.

---

## 🔧 Especificações Técnicas Implementadas

Seguindo os requisitos, implementei três pilares principais:

### 1. Controle de Versão com Git/GitHub

Estratégia GitFlow: Implementei a estratégia de ramificação GitFlow. A branch `main` é protegida e contém apenas o código de produção estável. Todo o desenvolvimento ativo acontece na branch `develop`.
  Commits Semânticos: Todo o histórico de "compromissos" (commits) foi feito usando o padrão de [Commits Semânticos](https://www.conventionalcommits.org/en/v1.0.0/). Isso organiza o histórico e deixa claro o que cada alteração fez (ex: `feat:`, `refactor:`, `fix:`, `style:`).
  Releases e Versionamento: O projeto está configurado para usar o Versionamento Semântico (`MAJOR.MINOR.PATCH`), permitindo a criação de `releases` (versões) claras e oficiais (ex: `v1.0.0`).

### 2. Acessibilidade (WCAG 2.1 Nível AA)

Fiz uma refatoração completa no HTML e CSS para garantir que o site seja 100% utilizável por todas as pessoas, incluindo aquelas que usam tecnologias assistivas.

Suporte a Leitores de Tela:**
     Adicionei `aria-label` descritivos em botões que só tinham ícones (como o botão do menu mobile).
     Substituí todos os textos `alt` genéricos das imagens por descrições ricas e detalhadas, explicando o que a imagem representa.
  Contraste de Cores:** Revisei todo o site e ajustei classes de texto (como `text-gray-600`) para garantir um contraste mínimo de `4.5:1` contra o fundo, como exige o nível AA. Usei `text-gray-700` ou `text-gray-800` na maioria dos casos.
  Navegação por Teclado:** Garanti que todos os links e botões sejam navegáveis usando apenas a tecla "Tab". Adicionei classes `focus:ring` personalizadas do Tailwind para que o foco seja sempre visível e siga a identidade visual do site.
  Modo Escuro Acessível:** Implementei um modo escuro completo e acessível. Usando a estratégia `darkMode: 'class'` do Tailwind e um pequeno script, o site detecta a preferência do sistema do usuário e aplica o tema escuro, mantendo todas as regras de contraste válidas.

### 3. Otimização para Produção

Minificação de CSS:** Como descrito acima, abandonei o CDN do Tailwind (que tem +3MB) e configurei um processo de "build". O arquivo `css/style.css` final, que é minificado, tem **apenas 10KB** (uma redução de mais de 99%!).
  Minificação de JavaScript:** O script do menu foi externalizado e minificado (`js/app.min.js`), garantindo que o navegador carregue o menor arquivo possível.
  Otimização de Imagens:** Todas as imagens do projeto foram convertidas para formatos modernos e leves, como `.webp`, que oferecem alta qualidade com um tamanho de arquivo muito menor.

---

## 💻 Como Rodar (Desenvolvimento)

Como este projeto agora tem um "passo de build" (o Tailwind precisa gerar o CSS), para rodar em modo de desenvolvimento, você precisa:

1.  Clonar o repositório: `git clone ...`
2.  Instalar as dependências: `npm install`
3.  Rodar o script de "watch" do Tailwind:
    ```bash
    npx tailwindcss -i ./css/input.css -o ./css/style.css --watch
    ```
4.  Abrir o arquivo `index.html` em seu navegador.

O comando `--watch` ficará monitorando seus arquivos. Qualquer alteração que você fizer no `index.html` (adicionando uma nova classe Tailwind) ou no `css/input.css` será automaticamente compilada para o `css/style.css`.

---

### Autora

**Íris Hanielle Pereira Rezende**

* [GitHub: @irisrezende](https://github.com/irisrezende)
