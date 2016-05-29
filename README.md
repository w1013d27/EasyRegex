## Easy Regex
- ported from [VerbalExpressions](https://github.com/VerbalExpressions/PHPVerbalExpressions)

EasyRegex is a PHP library that helps to construct hard regular expressions.  


```php
// some tests
use Koca\EasyRegex\EasyRegex;

$regex = new EasyRegex;

$regex  ->startOfLine()
        ->then("http")
        ->maybe("s")
        ->then("://")
        ->maybe("www.")
        ->anythingBut(" ")
        ->endOfLine();


if($regex->test("https://github.com/"))
    echo "valid url";
else
    echo "invalid url";

if (preg_match($regex, 'http://github.com')) {
    echo 'valid url';
} else {
    echo 'invalid url';
}


echo "<pre>". $regex->getRegex() ."</pre>";



echo $regex ->clean(array("modifiers" => "m", "replaceLimit" => 4))
            ->find(' ')
            ->replace("This is a small test http://somesite.com and some more text.", "-");

```

## Building the project and running the tests
The project supports Composer so you have to install [Composer](https://getcomposer.org/doc/00-intro.md#installation-nix) first before project setup.

    curl -sS https://getcomposer.org/installer | php
    php composer.phar install --dev
    ln -s vendor/phpunit/phpunit/phpunit.php phpunit
    ./phpunit
    

