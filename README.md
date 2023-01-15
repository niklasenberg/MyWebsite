# My Website

This portfolio is built with **Next.js** and a library called [Nextra](https://nextra.vercel.app/). It allows you to write Markdown and focus on the _content_ of your portfolio. I am selfhosting it on my [OKdo Rock 4C+](https://www.okdo.com/p/okdo-rock-4-model-c-4gb-single-board-computer-rockchip-rk3399-t-arm-cortex-a72/). It is publicly available at [niklasenberg.rocks](http://niklasenberg.rocks).

## Usages

- Nodejs + npm
- Nextjs

## Deployment

I use [forever](https://www.npmjs.com/package/forever) to deploy on a separate thread:

```forever start -c "npm start" ./```
