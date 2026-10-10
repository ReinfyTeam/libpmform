# libpmform

`libpmform` is a PHP library for creating JSON forms for PocketMine-MP servers.
It provides simple, modal, and custom forms with typed response callbacks.

## Requirements

- PHP 8.1 or newer
- PocketMine-MP API 5

## Installation

Install the library with Composer:

```sh
composer require reinfyteam/libpmform
```

For a PocketMine-MP plugin distributed as a PHAR, include the library through
the project's normal Virion packaging workflow. The project uses the
[DevTools repository](https://github.com/pmmp/DevTools) for plugin packaging;
the build tool version is selected by the consuming build configuration.

## Usage

```php
use czechpmdevs\libpmform\type\SimpleForm;

$form = new SimpleForm("Server menu", "Choose an option");
$form->addButton("Continue");
$form->setCallback(function($player, $response): void {
    if($response->isValid()) {
        $player->sendMessage("The selected form response was received.");
    }
});
$player->sendForm($form);
```

`ModalForm` creates a two-button confirmation form. `CustomForm` supports
labels, text inputs, toggles, and dropdowns. Form responses are represented by
`FormResponse`; a response is invalid when the player closes the form without
submitting it. Use `ignoreInvalidResponse()` when a form should ignore that
case.

## License

This project is distributed under the Apache License 2.0. See [LICENSE](LICENSE)
for the complete license text.
