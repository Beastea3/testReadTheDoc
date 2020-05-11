# Node Best Practices

**Structure App in Components**. Big software is hard to add some new features because developers can hardly not impact other modules of the software. Destructing the software into several minor partitions could be a good solution to this problem. In other words, grouping your code into components.

> Even who are skilled enough can hardly tame the beast and 'modularize' it.

Here is one more advantage of partitioning into micro-service, a minor change may require rebuild and redeployment of the whole system in a monolithic application. However, in a system which destructed into several partitions will be more convenient, the only job for you is to rebuild and redeploy the microservice of the change.

In my project, I use an original technical rule to divide my project files, such as controllers, services and models. But the recommended of the author is group files by components, it means one component does all the things related to the feature. For example, in this rule, you will put all the files related to user management in a directory named users, including controller and model. Of course, In each component, layers must be distinguished. Web access, service, and data access must be divided into different layers, this will benefit your ***test***, you can test your code by access your service, otherwise, you can only test by request.

**Wrapping common utilities as NPM packages** is a piece of awesome advice for me. Sometime, I will deploy a private NPM library and wrap some utils into NPM packages, this will make great advantages to our projects.

**Configure file awareness** is important when security is concerned, combine config file and environment variables will be useful in this problem, and there are many other advanced solutions:
    1. conf module NPM package;
    2. **Redis centralized cache will offer all servers the same config**;

**Writing code without a stack is a lot like driving a car without a brake pedal**

**Prefer Built_in Error Object** and there is a better way to do this:
    ```
    // Centralized error object that derives from Node’s Error
    function AppError(name, httpCode, description, isOperational) {
        Error.call(this);
        Error.captureStackTrace(this);
        this.name = name;
        //...Other properties assigned here
    };
    
    AppError.prototype.__proto__ = Error.prototype;
    
    module.exports.AppError = AppError;
    
    // Client throwing an exception
    if(user == null)
        throw new AppError(commonErrors.resourceNotFound, commonHTTPErrors.notFound, "further explanation", true)
    ```
    
    Will implement in the future(with http status);
    

**Distinguish operational error and programmer error** by expected or not.


**Handle errors centrally instead of Express middleware**, error handler may contain some logic stuff.

**Transfer errors into Documentations**, we can use Swagger and sentry, sentry used.

**Shut the process when required**, some apps should be restarted after error happened for a clean environment.


**Using a mature logger to make errors more visible**, the logs should be tagged by timestamp, and the format should be easy to digest.

**Test code by scripts**, using mocha for your app, either inner function or API request only, we can test API in the code below:
    ```
    it("Some function", function (done) {
      var invalidGroupInfo = {};
      httpRequest({
        method: 'POST',
        uri: "url/api/groups",
        resolveWithFullResponse: true,
        body: invalidGroupInfo,
        json: true
      }).then((response) => {
        // if we were to execute the code in this block, no error was thrown in the operation above
      }).catch(function (response) {
        expect(400).to.equal(response.statusCode);
        done();
      });
    });
    ```

**Catching unhandled promise rejections**, some errors will not automatically be caught by the framework. The solution below, to test in the future.
    ```
    process.on('unhandledRejection', (reason, p) => {
      // I just caught an unhandled promise rejection, since we already have fallback handler for unhandled errors (see below), let throw and let him handle that
      throw reason;
    });
    process.on('uncaughtException', (error) => {
      // I just received an error that was never handled, time to handle it and then decide whether a restart is needed
      errorManagement.handler.handleError(error);
      if (!errorManagement.handler.isTrustedError(error))
        process.exit(1);
    });
    ```
    
**Validating arguments early using a dedicated library**

**Delegate anything possible in the reverse proxy**, Node is powerful but weak in CPU intensive scenarios, so when we use node to server static files and zip the files to send, you will find something bad will happen. So better to use an Nginx or some other mature reverse proxies.



To be continued...






