# My PhpStorm Templates

These are my personal preferences for generated code.

If any template is missing it's because I use the default one.

## PHP File Header

```php

declare(strict_types=1);
```

## PHP Class

```php
<?php
#parse("PHP File Header.php")

#if (${NAMESPACE})
namespace ${NAMESPACE};

#end
class ${NAME} {
}
```

## PHP Constructor

```php
#if (${THROWS_DOC} != "")
/**
${THROWS_DOC}
*/
#end
public function __construct(${PARAM_LIST}) {${BODY}}
```

## PHP Getter Method

```php
public ${STATIC} function ${FIELD_NAME}()#if(${RETURN_TYPE}): ${RETURN_TYPE}#else#end
{
#if (${STATIC} == "static")
    return self::$${FIELD_NAME};
#else
    return $this->${FIELD_NAME};
#end
}
```

## PHP Setter Method

```php
public ${STATIC} function set${NAME}(#if (${SCALAR_TYPE_HINT})${SCALAR_TYPE_HINT} #end$${PARAM_NAME})#if (${VOID_RETURN_TYPE}): void #end
{
#if (${STATIC} == "static")
    self::$${FIELD_NAME} = $${PARAM_NAME};
#else
    $this->${FIELD_NAME} = $${PARAM_NAME};
#end
}
```

## PHP Fluent Setter Method

```php
public function set${NAME}(#if (${SCALAR_TYPE_HINT})${SCALAR_TYPE_HINT} #else#end$${PARAM_NAME})#if(${RETURN_TYPE}): self#else#end
{
    $this->${FIELD_NAME} = $${PARAM_NAME};
    return $this;
}

```

## PHPUnit Test Method

```php
/**
 * @test
 */
public function should${CAPITALIZED_NAME}(): void
{
}
```

# Live Templates

```xml
<template name="notImplemented" value="throw new \RuntimeException('Please, implement the method.');"
          description="not implemented exception" toReformat="true" toShortenFQNames="true">
  <context>
    <option name="PHP Statement" value="true" />
  </context>
</template>
```