## Redirect to Https protocol if not local environment

### Middleware class

```
<?php

namespace App\Http\Middleware;

use Closure;
use \Illuminate\Http\Request;

class ForceHttps
{
    /**
    * Handle an incoming request.
    *
    * @param  \Illuminate\Http\Request  $request
    * @param  \Closure  $next
    * @return mixed
    */
    public function handle($request, Closure $next)
    {

      if (!app()->environment('local')) {
          // for Proxies
          Request::setTrustedProxies([$request->getClientIp()]);

        if (!$request->isSecure()) {
         return redirect()->secure($request->getRequestUri());
        }
      }

      return $next($request);
    }
}
```

### Add in Kernal File

```
/**
* The application's global HTTP middleware stack.
*
* These middleware are run during every request to your application.
*
* @var ar

protected $middleware = [
    \App\Http\Middleware\ForceHttps::class
];
```