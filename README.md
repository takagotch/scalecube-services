### scalecbe-services
---
https://github.com/scalecube/scalecube-services

```java
Microservices seed = Microservices.builder().startAwait();

Microservices microservices =
  Microservices.builder()
    .discovery(
      self ->
        new ScalecubeServiceDiscovery(self)
          .options(opts -> opts.seedMembers(toAddress(seed.discovery().address())))
    .transport(ServiceTransports::rsocketServiceTransport)
    .services(new GreetingServiceTmpl())
    .startAwait();
  
  GreetingsService service = seed.call().api(GreetingsService.class);
  
  service.sayHello("joe").subscribe(consumer -> {
    System.out.println(consumer.message());
  });
)

@Service
public interface ExampleService {
  @ServiceMethod
  Mono<String> say Hello(String request);
  
  @ServiceMethod
  Flux<MyRespone> helloStream();
  
  @ServiceMethod
  Flux<MyResponse> helloBidrectional(Flux<MyRequest> request);
}

Microservices.builder()
  .discovery(options -> options.seeds(seed.discovery().address()))
  .services(...)
  
  .gateway(options -> new WebsocketGateway(options.id("ws").port(8080)))
  .gateway(options -> new HttpGateway(options.id("http").port(7070)))
  .gateway(options -> new RSocketGateway(options.id("rsws").port(9090)))
  
  .startAwait();
```

```
```

```
```
