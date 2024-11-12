---
banner: https://i.imgur.com/P83o6DJ.png/size/w=2000?exp=1731336428&sig=V5Z7LonHE2gpVsbsDcfCy6fBKGNlKv84hP4V6uVEWXg
title: Nextjs 13 Novidades
---
> O Next.js 13 traz uma série de melhorias que otimizam o desenvolvimento e o desempenho dos aplicativos. Confira os principais destaques desta versão:

## [**Diretório "app/"**](https://nextjs.org/blog/next-13#app-directory-beta)

O novo diretório "app/" introduz um sistema aprimorado de roteamento e layouts, permitindo reutilizar interfaces entre páginas e manter o estado sem re-renderizações desnecessárias. Destaques:

- **Layouts**: Permite definir layouts no sistema de arquivos, facilitando a reutilização de interfaces e mantendo a interatividade.
- **Server Components**: Nova arquitetura que combina renderizações no servidor e cliente para tornar os aplicativos mais rápidos e interativos.
- **Streaming**: Carregamento progressivo de conteúdo, exibindo partes da página enquanto outras ainda estão sendo processadas.

## [**Server Components**](https://nextjs.org/blog/next-13#server-components)

A introdução dos Server Components no diretório "app/" possibilita uma integração mais eficiente entre servidor e cliente. Isso resulta em carregamentos iniciais mais rápidos e redução do JavaScript enviado ao cliente, graças ao cache assíncrono do runtime.

## [**Streaming**](https://nextjs.org/blog/next-13#streaming)

Com renderização progressiva, o Next.js 13 permite que partes da página sejam exibidas instantaneamente, enquanto outras ainda estão carregando. Isso melhora a experiência do usuário, que pode interagir com a página antes de seu carregamento completo.

## [**Data Fetching**](https://nextjs.org/blog/next-13#data-fetching)

O novo hook `use()` substitui APIs como `getStaticProps` e `getServerSideProps`, e aproveita o "Suspense for Data Fetching" do React. Agora é possível buscar dados diretamente em layouts, páginas e componentes, com suporte a streaming, resultando em experiências mais interativas e eficientes no lado do cliente.

## [**Turbopack (alpha)**](https://nextjs.org/blog/next-13#introducing-turbopack-alpha)

O Next.js 13 introduz o Turbopack, sucessor do Webpack, construído em Rust. Ele é muito mais rápido e já suporta Server Components, TypeScript, JSX, CSS e muito mais.

## [**next/image**](https://nextjs.org/blog/next-13#nextimage)

O novo componente `Image` otimiza automaticamente as imagens, reduz o uso de JavaScript no cliente, melhora o desempenho e suporta carregamento "lazy" nativo.

## [**@next/font**](https://nextjs.org/blog/next-13#nextfont)

Com o novo sistema de fontes, é possível auto-hospedar fontes personalizadas e otimizar seu carregamento. Além disso, o sistema remove a dependência de fontes externas, aumentando a privacidade e o desempenho.

## [**Geração de Open Graph (OG)**](https://nextjs.org/blog/next-13#og-image-generation)

O Next.js 13 facilita a geração de Open Graphs dinâmicos com a biblioteca @vercel/og, aumentando o engajamento com imagens personalizadas criadas em tempo real.

## [**Atualizações na Middleware API**](https://nextjs.org/blog/next-13#middleware-api-updates)

Com melhorias na API de Middleware, agora é possível definir cabeçalhos diretamente e responder a solicitações sem precisar de `rewrite` ou `redirect`, facilitando a implementação de regras de roteamento personalizadas.

<section>
## [**Breaking Changes**](https://nextjs.org/blog/next-13#breaking-changes)

`test`

```js
Entre as mudanças importantes, 
destacam-se a atualização das versões mínimas do React e Node.js, a remoção de funcionalidades obsoletas e a definição de novos navegadores suportados.

```

---
</p>
Essas são as principais novidades do Next.js 13, uma versão focada em melhorar a experiência do desenvolvedor e proporcionar aplicativos web mais rápidos e interativos.