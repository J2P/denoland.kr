![deno](https://deno.land/deno_logo.png)

# Deno

Typescript 기반의 새로운 자바스크립트 런타임 [Deno](https://deno.land/) 에 대한 한국어 자료. Deno 와 관련 된 한국어 대화는 현재 [Seouljs](https://seoul.js.org/) 의 슬랙채널 #deno 에 진행 중. 관심 있다면 해당 링크를 사용. 아래 벤치마크 테스트는 캡처 된 HTML 이다. 그렇기 때문에 많은 정보를 제공하지 않는다. 추가 적인 정보는 [오리지널 벤치마크 테스트](https://deno.land/all_benchmark.html)를 참고한다.

| Linux & Mac                                                     | Windows                                                                                       |
| --------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| ![build](https://travis-ci.com/denoland/deno.svg?branch=master) | ![build](https://ci.appveyor.com/api/projects/status/yel7wtcqwoy0to8x/branch/master?svg=true) |

A new way to JavaScript

[denoland/deno: A new way to JavaScript](https://github.com/denoland/deno)

[denoland/deno_std: deno standard modules](https://github.com/denoland/deno_std)

[denoland/deno_install: Deno Binary Installer](https://github.com/denoland/deno_install)

[denoland/registry](https://github.com/denoland/registry)

[Documentation](https://github.com/denoland/deno/blob/master/Docs.md)

[API Reference](https://deno.land/typedoc/index.html)

[denolib/awesome-deno: 🎉A curated list of awesome things related to Deno](https://github.com/denolib/awesome-deno)

# Getting started

Install Deno into ~/.deno/bin

## With Shell

```sh
curl -L https://deno.land/x/install/install.sh | sh
export PATH=$HOME/.deno/bin:$PATH
```

## With PowerShell

```sh
iex (iwr https://deno.land/x/install/install.ps1)
```

Try a Deno program. Install by bash alias. This one serves a local directory in HTTP.

```sh
alias file_server="deno \
  https://deno.land/x/http/file_server.ts --allow-net"
```

Run it:

```sh
% file_server .
Downloading https://deno.land/x/http/file_server.ts...
[...]
HTTP server listening on http://0.0.0.0:4500/
```

And if you ever want to upgrade to the latest published version:

```sh
file_server --reload
```

# Benchmarks

## Execution time

This shows how much time total it takes to run a few simple deno programs: [tests/002_hello.ts](https://github.com/denoland/deno/blob/master/tests/002_hello.ts) and [tests/003_relative_import.ts](https://github.com/denoland/deno/blob/master/tests/003_relative_import.ts). For deno to execute typescript, it must first compile it to JS. A warm startup is when deno has a cached JS output already, so it should be fast because it bypasses the TS compiler. A cold startup is when deno must compile from scratch.

![bechmarks](/images/execution-time.png)

## Throughput

Time it takes to pipe a certain amount of data through Deno. [echo_server.ts](https://github.com/denoland/deno/blob/master/tests/echo_server.ts) and [cat.ts](https://github.com/denoland/deno/blob/master/tests/cat.ts) Smaller is better.

![bechmarks](/images/throughput.png)

## Req/Sec

Tests HTTP server performance. 10 keep-alive connections do as many hello-world requests as possible. Bigger is better.

- [deno](https://github.com/denoland/deno/blob/master/tests/http_bench.ts) is a fake http server that doesn't parse HTTP. It is comparable to [node_tcp](https://github.com/denoland/deno/blob/master/tools/node_tcp.js).
- [deno_net_http](https://github.com/denoland/deno_std/blob/master/http/http_bench.ts) is a web server written in TypeScript. It is comparable to [node_http](https://github.com/denoland/deno/blob/master/tools/node_http.js).
- [hyper](https://github.com/denoland/deno/blob/master/tools/hyper_hello.rs) is a Rust HTTP server and represents an upper bound.

![bechmarks](/images/req-sec.png)

## Executable size

deno ships only a single binary. We track its size here.

![bechmarks](/images/executable-size.png)

## Thread count

How many threads various programs use.

![bechmarks](/images/thread-count.png)

## Syscall count

How many total syscalls are performed when executing a given script.

![bechmarks](/images/syscall-count.png)

## Travis

![bechmarks](/images/travis.png)

How long for Travis CI to return a green status for pull requests.

## References

[All benchmark data](https://deno.land/all_benchmark.html)

# License

저작권은 모두 원저자들에게 있다. 번역을 포함한 다른 자료들의 저작권은 아래와 같다.

MIT @ denoland.kr
