# Tailscale, Caddy, Automatic SSL

Ok, this is a very simple example of what I have set up based on the tailscale docker image example.

## To use

- docker-compose.yml needs a TS_AUTHKEY to join your tailnet. And you'll want to change your TS_HOSTNAME to whatever you want to call this virtual node. In this example it's ollama.blah-blah.ts.net
- Caddyfile configures what ports get proxied and how. This one is proxying 11434 and 3000 for ollama and openweb-ui respectively. But you can use whatever ports you want.

The volumes should be configured so tailscale will authenticate the first time it connects and saves that information for future logins. There is also mapping so Caddy can access the tailscaled.sock. That's needed so it can automagically create ssl certs and populate them.
