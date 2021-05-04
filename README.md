# cloudflare-worker-reverse-proxy

This is a reverse proxy implemented using [Cloudflare workers](https://workers.cloudflare.com/).

# Quickstart

1. Clone this repo
```
git clone 
```

2. Install dependencies
```
npm i
```

3. Authorize yourself with your Cloudflare account
```
npm run login
```

4. Make a copy of `wrangler.toml.example` and name it `wrangler.toml`. Set `account_id` in `wrangler.toml`:
```
account_id = [Account ID value from login]
```
Optionally, rename the Cloudflare worker in `wrangler.toml`:
```
name = [Cloudflare worker name]
```

5. Test that it works
```
npm run preview
```

6. Publish the code to Cloudflare
```
npm run publish
```

# Usage

Proxy any request through the Cloudflare worker by passing the **entire** URL as a query string to the Cloudflare worker. So if your Cloudflare worker domain is 
```
https://x.y.workers.dev
```
and the request you want to proxy is
```
https://api.example.com?param1=test1&param2=test2
```
then the final request URL should be
```
https://x.y.workers.dev?https://api.example.com?param1=test1&param2=test2
```

# Caching

For simplicity, this code does not configure the `cf` headers on the `fetch` request that is sent to the Cloudflare proxy. Set the `cf` request headers to configure the Cloudflare worker's behavior on caching. See: [Cache using fetch](https://developers.cloudflare.com/workers/examples/cache-using-fetch). 
