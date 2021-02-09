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

#### Decorators
- Nest provides decorators for all of the standard HTTP methods: @Get(), @Post(), @Put(), @Delete(), @Patch(), @Options(), and @Head(). In addition, @All() defines an endpoint that handles all of them.

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
  
