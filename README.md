# Laravel strict coding standard

[PHP_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer) coding standards for Laravel,
do force developers not to use bad design decisions that are supported
by [Laravel](https://laravel.com)

## Sniffs included in this standard

### LaravelStrictCodingStandard.Laravel.DisallowUseOfGlobalFunctions

* checks for functions that are declared in

  * `vendor/laravel/framework/src/Illuminate/Foundation/helpers.php`
  * `vendor/laravel/framework/src/Illuminate/Support/helpers.php`

### LaravelStrictCodingStandard.Laravel.DisallowUseOfFacades

* checks for usage of Laravel Facades (including Real-time facades)
* if not configured it will use default path for `Illuminate\Foundation\Application`
instance at `bootstrap/app.php`

so for default `Illuminate\Foundation\Application` instance use
```xml
<rule ref="LaravelStrictCodingStandard.Laravel.DisallowUseOfFacades"/>
```
to override, do this

```xml
<rule ref="LaravelStrictCodingStandard.Laravel.DisallowUseOfFacades">
    <properties>
        <property name="laravelApplicationInstancePath" type="string" value=".nonDefaultFolder/application.php"/>
    </properties>
</rule>
```
we need this instance, so we can get all Facades and Aliases that are potentially used in the app
