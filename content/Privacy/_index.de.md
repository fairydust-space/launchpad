---
title: "Privacy"
date: 2020-07-07T19:00:00Z
draft: false
---

## What we do to protect your privacy

### Webserver logs

In most cases we do not log anything.
In `nginx` this means

```nginx
access_log off;
```

In case we have to log more (for example for debugging), we only log errors (requests with a status code in the  [4xx or 5xx](https://http.cat/)) range.

- timestamp
- the request URL (so we know where the error occured)
- the error code
- user-agent (the type of browser/client used)
- the encryption used (TLS cipher suite)

This is the `nginx` log format we use for that:

```nginx
map $status $only_errors {
    ~^[23] 0;
    default 1;
}

log_format matrix '[$time_local] "$request" $status "$http_user_agent" "$ssl_protocol/$ssl_cipher"';
```

### Referrer Policy

If you klick on a link to an external website your browser will usually send a `referer` header, to tell the destination site where you came from. (Yes, that typo is [actually in the spec](https://tools.ietf.org/html/rfc2616#section-14.36).) It's possible to instruct browsers not to do that, which is what we always do.

In `nginx` we always send this response header:

```nginx
Referrer-Policy: no-referrer
```

This commands browsers not to send a `referer` header in any case when using our provided [Element/Web Instance](https://chat.fairydust.space/) or this website.
This does *not* necessarily apply if you use a 3rd party hosted webchat client.

### Tor friendly

If you prefer [Tor Browser](https://www.torproject.org/download/) to use our website or chat, you're encouraged to do so. Likewise if you're using any Matrix client of your choice via Tor as a SOCKS proxy. Currently we do not (yet) provide an `.onion` service.

### 3rd party web chats

If you prefer to use a different chat webinterface than the one we provide, you're welcome to do so. We also support client autoconfiguration.

### Federated Learning of Cohorts (FLoC) tracking

We send a [Permissions-Policy Header](https://www.w3.org/TR/permissions-policy-1/) that instructs browsers to turn off [Federated Learning of Cohorts (FLoC)](https://github.com/WICG/floc#opting-out-of-computation).

```
Permissions-Policy: interest-cohort=()
```
