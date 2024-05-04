
## Wordpress Coding Standard (WPCS using PHPCS - PHP Coding Standard)

> [!NOTE]
> - Extension PHP Sniffer & Beautifier support `phpcs` and `phpbcf`
> - Extension phpcs only support `phpcs`
> - Ignore Configure Open User Settings (JSON), the extension has auto configuration capability 

- VS Code Extension using PHP Sniffer & Beautifier, publisher: Samuel Hilson 
![image](https://github.com/si294r/howto-wp/assets/10229458/8169f083-2e70-46a1-b4eb-bade16a14b96)

- ~~VS Code Extension using phpcs (PHP CodeSniffer for Visual Studio Code), publisher: shevaua~~
![image](https://github.com/si294r/howto-wp/assets/10229458/84ec2961-20b1-4e98-81ea-bbed8b1ee130)
 
- run `composer config allow-plugins.dealerdirect/phpcodesniffer-composer-installer true`
- run `composer require --dev wp-coding-standards/wpcs:"^3.0"`
- ~~in VS Code, goto >Preferences: Open User Settings (JSON); file `settings.json`~~
```
{
	// PHPCS
	"phpcs.enable": true,
	"phpcs.standard": "WordPress",
	"phpcs.executablePath": "./vendor/bin/phpcs",
	"phpcs.showWarnings": true,
	"phpcs.composerJsonPath": "composer.json",
}
```
- apply `[plugin-folder]\phpcs.xml`
```
<?xml version="1.0"?>
<ruleset name="Custom WordPress Coding Standard">
  <rule ref="WordPress">
    <exclude name="Generic.Files.LineEndings.InvalidEOLChar"/>
    <exclude name="Generic.Commenting.DocComment.MissingShort"/>
    <exclude name="Squiz.Commenting.FileComment.Missing"/>
    <exclude name="Squiz.Commenting.VariableComment.Missing"/>
    <exclude name="Squiz.Commenting.FunctionComment.Missing"/>
  </rule>
</ruleset>
```
- example manual command to check coding standard on terminal :
```
vendor/bin/phpcs -s --standard=phpcs.xml includes/class-rkas.php
vendor/bin/phpcbf -s --standard=phpcs.xml includes/class-rkas.php
```
