## IsAdmin Middleware for Laravel

### IsAdmin Middleware class

```
<?php

namespace App\Http\Middleware;

use Closure;

class IsAdmin
{
    /**
    * Handle an incoming request.
    *
    * @param  \Illuminate\Http\Request $request
    * @param  \Closure $next
    * @return mixed
    */

    public function handle($request, Closure $next)
    {
            if (\Auth::user() && \Auth::user()->type == 'ADMIN') {
            return $next($request);
        }

        return redirect('/dashboard');
    }

}
```

### Add in kernal file in route middlewares

```
protected $routeMiddleware = [
'admin' => \App\Http\Middleware\IsAdmin::class,
];
```

### Usage

```
public function __construct()
{
    $this->middleware(['auth']);
}
```