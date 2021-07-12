---
title: "Privacy"
date: 2020-07-07T19:00:00Z
draft: false
---

## Was wir unternehmen, um Deine Privatsphäre zu schützen

### Webserver logs

In den meisten Fällen wird nichts aufgezeichnet
In `nginx` bedeutet das:

```nginx
access_log off;
```

Wenn wir mehr aufzeichnen müssen (zum Beispiel zur Fehlerbehebung), zeichnen wir nur Fehlermeldungen auf (Anfragen mit Status Codes im Bereich von [4xx oder 5xx](https://http.cat/)).

- Zeitstempel
- Die angefragte URL (damit wir wissen, wo der Fehler aufgetreten ist)
- Der Fehlercode
- User-agent (der verwendete Browser / Client)
- Die verwendete Verschlüsselung (TLS cipher suite)

Dies ist das `nginx` Logging-Format, welches wir dafür verwenden

```nginx
map $status $only_errors {
    ~^[23] 0;
    default 1;
}

log_format matrix '[$time_local] "$request" $status "$http_user_agent" "$ssl_protocol/$ssl_cipher"';
```

### Referrer Strategie

Wenn Du auf einen Link zu einer externen Website klickst, sendet Dein Browser üblicherweise einen `referer` header, um der Zielseite mitzuteilen, woher Du gekommen bist. (Ja, dieser Schreibfehler ist [effektiv in der Spezifikation](https://tools.ietf.org/html/rfc2616#section-14.36).) Es ist möglich, den Browser zu instruieren, dies zu unterlassen. Dies handhaben wir jeweils so.

In `nginx` senden wir immer diesen Response Header:

```nginx
Referrer-Policy: no-referrer
```

Dies teilt dem Browser mit, den `referer` Header niemals zu senden, wenn unsere [Element/Web Instanz](https://chat.fairydust.space/) oder diese Website verwendet wird.
Dies trifft *nicht* automatisch zu, wenn ein Webchat Client eines Drittanbieters genutzt wird.

### Tor-freundlich

Wenn Du den [Tor Browser](https://www.torproject.org/download/) bevorzugst, um unsere Website oder Chat zu nutzen - Nur zu! Das selbe gilt, wenn Du einen Matrix Client Deiner Wahl via Tor als SOCKS proxy verwendest. Momentan bieten wir (noch) keinen `.onion` Service an.

### Web-Chat Drittanbieter

Wenn Du einen Web-Chat Drittanbieter verwenden möchtest, ist dies ebenfalls kein Problem. Wir untersützen ausserdem die Client-Autokonfiguration.

### Federated Learning of Cohorts (FLoC) tracking

Wir senden einen [Permissions-Policy Header](https://www.w3.org/TR/permissions-policy-1/), der den Browser instruiert, [Federated Learning of Cohorts (FLoC)](https://github.com/WICG/floc#opting-out-of-computation) zu deaktivieren.

```
Permissions-Policy: interest-cohort=()
```
