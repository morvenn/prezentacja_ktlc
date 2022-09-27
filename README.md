# Presentation about CSS

This is a presentation about slightly more advanced aspects of
CSS language.

This presentation uses [reveal.js presentation engine](https://revealjs.com). For more info see [here](./README-reveal.md).

In order to work locally on this presentation, you need to use a HTTP server, because without it, reveal.js can't read Markdown files. There are many solutions to that; personally I use `es-dev-server`. From the main folder of your presentation (given that `nodejs` is installed in your computer), run this command:

```
npx es-dev-server --node-resolve --watch
```

It will spawn a HTTP server, usually accessible at `http://localhost:8000`. You will be able to see your progress on your presentation there.
