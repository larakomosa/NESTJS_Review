# NESTJS_Review
- Combiness elements  of OOP, FP and FRP
- Makes use of robust HTTP Server frameworks like Express.  

## Core Files
- app.contoller.ts
  - A basic controller with a single route
- app.controller.spec.ts  
  - The unit tests for the controller
- app.module.ts  
  - The root module of the applicatios
- app.service.ts 
 - A basic service with a single method
- main.ts
  - The entry file of the application which uses the core function NestFactory to create the Nest application instance 
  
## Basics
#### Controllers
 - responsible for handling incoming requests and returning responses to the client- routing mechinism controls which controller reveives which requests. 
 - In order to create a basic controller, we use calsses and decorators.  Decorators associate classes with metadata and enableto to create routing map.
  
#### Routing
 - @Controller decorater is required to define a basic controller.  
 - The @Get() HTTP request method decorator before the findAll() method tells Nest to create a handler for a specific endpoint for HTTP requests. 
 -  the path includes both the optional controller path prefix and any path string declared in the request method decorator. For example, a path prefix of customers combined with the decorator @Get('profile') would produce a route mapping for requests like GET /customers/profile.
 - Request object#
    - Handlers often need access to the client request details. Nest provides access to the request object of the underlying platform (Express by default). We can        access the request object by instructing Nest to inject it by adding the @Req() decorator to the handler's signature. 
- The response status code is always 200 by default, except for POST requests which are 201. 
#### Decorators
- Nest provides decorators for all of the standard HTTP methods: @Get(), @Post(), @Put(), @Delete(), @Patch(), @Options(), and @Head(). In addition, @All() defines an endpoint that handles all of them.
- To specify a custom response header, you can either use a @Header() decorator or a library-specific response object (and call res.header() directly).
-Other Decorators:
@Request(), @Req()	req
@Response(), @Res()*	res
@Next()	next
@Session()	req.session
@Param(key?: string)	req.params / req.params[key]
@Body(key?: string)	req.body / req.body[key]
@Query(key?: string)	req.query / req.query[key]
@Headers(name?: string)	req.headers / req.headers[name]
@Ip()	req.ip
@HostParam()	req.hosts

#### Providers 
- The main idea of a provider is that it can inject dependencies; this means objects can create various relationships with each other, and the function of "wiring up" instances of objects can largely be delegated to the Nest runtime system. A provider is simply a class annotated with an @Injectable() decorator.
- Provider registration
- Now that we have defined a provider (CatsService), and we have a consumer of that service (CatsController), we need to register the service with Nest so that it can perform the injection. We do this by editing our module file (app.module.ts) and adding the service to the providers array of the @Module() decorator.
 
#### Modules
- A module is a class annotated with a @Module() decorator. The @Module() decorator provides metadata that Nest makes use of to organize the application structure.
- Each application has at least one module, a root module. The root module is the starting point Nest uses to build the application graph - the internal data structure Nest uses to resolve module and provider relationships and dependencies. While very small applications may theoretically have just the root module, this is not the typical case. We want to emphasize that modules are strongly recommended as an effective way to organize your components. Thus, for most applications, the resulting architecture will employ multiple modules, each encapsulating a closely related set of capabilities.
