# Day 02: Reverse Proxy Configuration

## 🔄 Architecture
We set up Nginx to act as a **Reverse Proxy**.
- **Client** requests `http://site1.lab/app/`.
- **Nginx** receives request on Port 80.
- **Nginx** forwards request to `127.0.0.1:8080` (Python App).
- **Python App** responds to Nginx.
- **Nginx** sends response back to Client.

## Security Concept: Localhost Binding
I bound the Python app to `127.0.0.1` instead of `0.0.0.0`.
- **Why?** This will ensures the app is **not reachable** directly from the internet.
- Attackers cannot bypass Nginx to hit the app directly. They *must* go through our Nginx rules (logs, firewalls, rate limits).

## Configuration Snippet
```nginx
location /app/ {
    proxy_pass [http://127.0.0.1:8080/](http://127.0.0.1:8080/);
}
