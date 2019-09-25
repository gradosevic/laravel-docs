# laravel-docs

## CREATE CUSTOM SERVICE PROVIDER FOR DI

```<?php
namespace App\Providers;
  
use Illuminate\Support\ServiceProvider;
use App\Library\Services\DemoOne;
  
class EnvatoCustomServiceProvider extends ServiceProvider
{
    public function boot()
    {
    }
  
    public function register()
    {
        $this->app->bind('App\Library\Services\DemoOne', function ($app) {
          return new DemoOne();
        });
    }
}
```
```
<?php
namespace App\Library\Services;
  
class DemoOne
{
    public function doSomethingUseful()
    {
      return 'Output from DemoOne';
    }
}
```
```
<?php
namespace App\Http\Controllers;
  
use App\Http\Controllers\Controller;
use App\Library\Services\DemoOne;
  
class TestController extends Controller
{
    public function index(DemoOne $customServiceInstance)
    {
        echo $customServiceInstance->doSomethingUseful();
    }
}

```


## Laravel local package
Add this to composer.json

```
repositories:[
  {
    type: vcs,
    url: /path/to/local/repo
  }
]
```

## Autoload helpers from package.json

```
autoload:{
  files:[
    "app/helpers.php"
  ]
}
```
