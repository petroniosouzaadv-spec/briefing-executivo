# Pacote pronto para GitHub Pages com automação

Este projeto já está configurado para uso como relatório online em HTML estático, com favicon integrado e workflow de deploy para GitHub Pages.

## Estrutura

- `index.html` — página principal do relatório
- `.nojekyll` — evita processamento Jekyll
- `.github/workflows/deploy-pages.yml` — publica no GitHub Pages
- `favicon.ico`
- `favicon-16x16.png`
- `favicon-32x32.png`
- `apple-touch-icon.png`
- `android-chrome-192x192.png`
- `android-chrome-512x512.png`
- `site.webmanifest`

## Como publicar

1. Crie um repositório no GitHub.
2. Envie todos os arquivos deste pacote para a raiz do repositório.
3. No GitHub, vá em **Settings > Pages**.
4. Em **Build and deployment**, selecione **GitHub Actions**.
5. Faça o commit inicial.
6. Aguarde o workflow concluir. O GitHub Pages vai gerar a URL pública do site.

## Como a automação deve funcionar

A automação pode sobrescrever o arquivo `index.html` a cada execução.
Depois disso, ela deve fazer:

1. commit
2. push para a branch `main`

Cada push dispara um novo deploy do GitHub Pages.

## Observação importante sobre automação

Se a atualização do `index.html` for feita por uma automação dentro do próprio GitHub Actions usando apenas `GITHUB_TOKEN`, esse commit pode não disparar um novo build do Pages automaticamente.

Nesse cenário, o caminho mais seguro é um destes:

1. a própria automação já atualizar e publicar no mesmo workflow; ou
2. a automação fazer push com um PAT; ou
3. a automação rodar fora do GitHub e fazer push normal no repositório.

## Observação de segurança

O conteúdo atual do `index.html` aparenta conter dados operacionais e sensíveis.
Se o repositório for publicado como site público, esse conteúdo poderá ficar acessível na internet.

Revise isso antes de publicar se houver risco de exposição indevida.
