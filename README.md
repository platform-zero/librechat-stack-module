# LibreChat stack module

LibreChat is the Platform Zero chat/PWA client at `ai.datamancy.net`.
It uses Keycloak OIDC for human login and the private P0 model gateway for
each human's OpenRouter key and selected model. `p0/default` is direct model
chat; `p0/agent` runs Pi in the agent selected with `p0 agent select NAME` or
the personal control GUI. MongoDB and Meilisearch are
reachable only on `librechat-internal`; Caddy reaches the app on its own network.

The model gateway authenticates this server with `P0_MODEL_GATEWAY_SECRET`
and maps `{{LIBRECHAT_USER_OPENIDID}}` to the immutable Keycloak subject. The
browser does not receive the OpenRouter key. Secrets are supplied by the site
bundle; no secret values belong in this repository.
