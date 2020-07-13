## Airtable as CMS

Boilerplate code for a very simple frontend that uses [Airtable](https://airtable.com/) as a CMS. Built using `vue-cli`. 

This is a port/clone of https://github.com/Kallirroi/airtable_as_cms, ported to Vue.

## Getting started with development

In order to authenticate to Airtable API, you have to create a `.env` file in the root directory. Copy `.env.example` to `.env` and fill in the parameters.

Then:
- `npm install` to install dependencies
- `npm run serve` to create a hot-reloading server for development on `localhost:8080`

If you change the details above, you need to restart your server. 

## How to style

Vue styling can be scoped to each component, so AirtableDisplayExample.vue contains the css for that specific component.

## How to deploy

Documentation TBD; to use [Vercel](https://vercel.com/) see [this documentation](https://vercel.com/guides/deploying-vuejs-to-vercel). 

Don't forget to set up the `env` variables (both services offer a way to do that on their platform GUI).


