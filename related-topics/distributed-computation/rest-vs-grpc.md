# REST vs gRPC

{% hint style="info" %}
__[_Is gRPC better than REST? Where to use it?_](https://dev.to/techschoolguru/is-grpc-better-than-rest-where-to-use-it-3blg)__
{% endhint %}

### _Overview Comparison_

| __                  | gRPC                     | REST                  |
| ------------------- | ------------------------ | --------------------- |
| **Protocol**        | HTTP/2 (faster)          | HTTP/1.1 (slower)     |
| **Payload**         | Protobuf (binary, small) | JSON (text, large)    |
| **API contract**    | Typed, required (.proto) | Optional (OpenAPI)    |
| **Code generation** | Built-in (protoc)        | Third-party (Swagger) |
| **Security**        | TLS/SSL                  | TLS/SSL               |
| **Streaming**       | Bidirectional            | Client to Server      |
| **Browser support** | Limited                  | Yes                   |

### When to use each gRPC?

* Microservices
  * Low latency + high throughput
  * Strong API contracts
* Services implemented in different languages
* Streaming is needed.
* Network constrained environments
  * Lighter weight messages

### Main pains of gRPC

* Contract management and code generation
* A strict API contract in environments with regular updates in contracts.
