# Create a proxy for any web address

**BE SURE TO PASS A Host HEADER**

After starting this container:

```
docker run --rm -it -p 8474:8474 -p 3000-3120:3000-3120 \
	-v `pwd`:/etc/toxiproxy/ ghcr.io/shopify/toxiproxy -host 0.0.0.0 -config /etc/toxiproxy/toxiproxy.json
```

`curl -H "Host: ifconfig.me" localhost:3000`

You can then use the toxiproxy-cli to add another proxy using any exposed port (i.e. 3000, 3001...3120)

```
toxiproxy-cli c goog -l :3001 -u www.google.com:443
```

For TLS proxies, add to `/etc/hosts`:

```
127.0.0.1	proxied.google.com
```
