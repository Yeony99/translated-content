---
title: OPTIONS
slug: Web/HTTP/Methods/OPTIONS
tags:
  - HTTP
  - 요청 메소드
translation_of: Web/HTTP/Methods/OPTIONS
---
{{HTTPSidebar}}

**HTTP `OPTIONS` method** 는 목표 리소스와의 통신 옵션을 설명하기 위해 사용됩니다. 클라이언트는 OPTIONS 메소드의 URL을 특정지을 수 있으며, aterisk(\*) 를 통해 서버 전체를 선택할 수 있습니다.

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">Request has body</th>
      <td>No</td>
    </tr>
    <tr>
      <th scope="row">Successful response has body</th>
      <td>Yes</td>
    </tr>
    <tr>
      <th scope="row">{{Glossary("Safe")}}</th>
      <td>Yes</td>
    </tr>
    <tr>
      <th scope="row">{{Glossary("Idempotent")}}</th>
      <td>Yes</td>
    </tr>
    <tr>
      <th scope="row">{{Glossary("Cacheable")}}</th>
      <td>No</td>
    </tr>
    <tr>
      <th scope="row">Allowed in HTML forms</th>
      <td>No</td>
    </tr>
  </tbody>
</table>

## Syntax

```
OPTIONS /index.html HTTP/1.1
OPTIONS * HTTP/1.1
```

## Examples

### Identifying allowed request methods

curl을 이용하여 OPTIONS 요청을 서버에 보냄으로써 서버에서 지원하는 method를 확인할 수 있다.

```
curl -X OPTIONS http://example.org -i
```

요청을 보내면, 응답에 {{HTTPHeader("Allow")}}헤더가 포함되어서 오는데, 이를 통해 허용되는 메소드를 확인할 수 있다.

```
HTTP/1.1 200 OK
Allow: OPTIONS, GET, HEAD, POST
Cache-Control: max-age=604800
Date: Thu, 13 Oct 2016 11:45:00 GMT
Expires: Thu, 20 Oct 2016 11:45:00 GMT
Server: EOS (lax004/2813)
x-ec-custom-error: 1
Content-Length: 0
```

### Preflighted requests in CORS

In [CORS](/ko/docs/Web/HTTP/Access_control_CORS) 에서, `OPTIONS` 메소드를 통해 프리플라이트 요청 (preflight, 사전 전달), 즉 사전 요청을 보내 서버가 해당 parameters를 포함한 요청을 보내도 되는지에 대한 응답을 줄 수 있게 한다.

{{HTTPHeader("Access-Control-Request-Method")}} 헤더는 프리플라이트 요청의 일부분으로 서버에게 실제 요청이 전달 될 때 `POST` 요청 메소드로 전달될 것 임을 명시한다.

{{HTTPHeader("Access-Control-Request-Headers")}} 헤더는 서버에게 실제 요청이 전달될 때 `X-PINGOTHER` 와 `Content-Type` custom headers 와 함께 전달될 것 임을 명시한다. 서버는 그럼 이러한 요구사항들에 맞춰 요청을 수락할 것인지 정할 수 있다.

```
OPTIONS /resources/post-here/ HTTP/1.1
Host: bar.other
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Connection: keep-alive
Origin: http://foo.example
Access-Control-Request-Method: POST
Access-Control-Request-Headers: X-PINGOTHER, Content-Type
```

서버는 {{HTTPHeader("Access-Control-Allow-Methods")}}로 응답하고, `POST`, `GET`, 그리고 `OPTIONS` 메소드를 통해서 해당하는 자원을 문의 (query) 할 수 있다고 알려준다. 이 헤더는 {{HTTPHeader("Allow")}} 응답 헤더와 비슷하지만 반드시 CORS 에 한해서만 사용된다.

```
HTTP/1.1 200 OK
Date: Mon, 01 Dec 2008 01:15:39 GMT
Server: Apache/2.0.61 (Unix)
Access-Control-Allow-Origin: http://foo.example
Access-Control-Allow-Methods: POST, GET, OPTIONS
Access-Control-Allow-Headers: X-PINGOTHER, Content-Type
Access-Control-Max-Age: 86400
Vary: Accept-Encoding, Origin
Content-Encoding: gzip
Content-Length: 0
Keep-Alive: timeout=2, max=100
Connection: Keep-Alive
Content-Type: text/plain
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat("http.methods.OPTIONS")}}

## See also

- {{HTTPHeader("Allow")}} header
- [CORS](/ko/docs/Web/HTTP/Access_control_CORS)
