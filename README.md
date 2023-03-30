# cors-proxy

Implementing a CORS proxy using Cloudflare Workers to overcome the limitations of the Notion API, which does not allow cross-origin requests by default.

See issue here: https://github.com/makenotion/notion-sdk-js/issues/96
<p align="center">
<img width="800" src="https://user-images.githubusercontent.com/58854510/228769809-a5ea4c62-86ad-46f8-b617-ab11909c4b08.png" />
</p>

## How is this deployed? 
This worker is deployed on Clouflare. 

Steps to set this up: 
1. Create a Cloudflare account at https://dash.cloudflare.com/
2. Under Workers tab, click on `Create a Service`
<p align="center">
<img width="600" src="https://user-images.githubusercontent.com/58854510/228771145-35300f11-d089-4e13-8385-761ae00917d1.png" />
</p>

3. Name the service, and click `Create Service`
<p align="center">
<img width="600" src="https://user-images.githubusercontent.com/58854510/228770920-b2992c38-5731-46fd-9aef-e74450dd83fc.png" />
</p>

4. Click on `Quick Edit`

5. Paste the `index.js` file into the code editor (modified from https://developers.cloudflare.com/workers/examples/cors-header-proxy/)

6. Click Deploy! 

Now any requests made to `https://demo.zinean00.workers.dev/cors/<url>` will forward the requests to `<url>` while adding the "Access-Control-Allow-Origin: *" in the reply header.

This then allows us to make requests to Notion API through a browser! 
