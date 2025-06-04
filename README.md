# Laravel Visual Builder

A powerful, AI-powered visual builder for Laravel applications that enables drag-and-drop interface creation, API generation, and multi-auth support.

## Features

- 🎨 Drag-and-drop interface builder
- 🔄 AI-powered API generation
- 🔐 Multi-auth & role-permission system
- 🎯 Frontend & backend support
- 🤖 AI automation features
- 📚 Comprehensive documentation

## Requirements

- PHP 8.1 or higher
- Laravel 11 or 12
- Node.js 16 or higher (for frontend assets)
- Composer

## Installation

1. Install the package via Composer:

```bash
composer require laravel-builder/visual-builder
```

2. Publish the package assets:

```bash
php artisan vendor:publish --provider="LaravelBuilder\VisualBuilder\VisualBuilderServiceProvider"
```

3. Run the migrations:

```bash
php artisan migrate
```

4. Install frontend dependencies:

```bash
npm install
npm run build
```

## Configuration

The package configuration file is located at `config/visual-builder.php`. You can customize various aspects of the builder:

```php
return [
    'frontend' => [
        'framework' => env('VISUAL_BUILDER_FRONTEND', 'livewire'),
        'theme' => env('VISUAL_BUILDER_THEME', 'light'),
    ],
    'ai' => [
        'enabled' => env('VISUAL_BUILDER_AI_ENABLED', true),
        'provider' => env('VISUAL_BUILDER_AI_PROVIDER', 'openai'),
        'model' => env('VISUAL_BUILDER_AI_MODEL', 'gpt-4'),
    ],
    // ... more configuration options
];
```

## Usage

### Building Pages

```php
use LaravelBuilder\VisualBuilder\Facades\VisualBuilder;

// Create a new page
$page = VisualBuilder::buildPage([
    'name' => 'dashboard',
    'layout' => 'admin',
    'components' => [
        // ... component configuration
    ],
]);
```

### Generating APIs

```php
// Generate a RESTful API
$api = VisualBuilder::buildApi([
    'name' => 'users',
    'version' => 'v1',
    'endpoints' => [
        // ... endpoint configuration
    ],
]);
```

### Managing Authentication

```php
// Set up multi-auth
$auth = VisualBuilder::buildAuth([
    'guards' => [
        'web' => [
            'driver' => 'session',
            'provider' => 'users',
        ],
        'api' => [
            'driver' => 'sanctum',
            'provider' => 'users',
        ],
    ],
]);
```

### Using AI Features

```php
// Get AI suggestions for a model
$suggestions = VisualBuilder::generateAISuggestions('User model with name, email, and role fields');

// Generate CRUD structure
$crud = VisualBuilder::predictCrudStructure('Product');
```

## Available Commands

- `php artisan build:page` - Create a new page
- `php artisan build:api` - Generate API endpoints
- `php artisan build:auth` - Set up authentication
- `php artisan build:component` - Create a new component
- `php artisan build:menu` - Generate a menu structure

## Frontend Integration

The package supports both Livewire and Vue.js for frontend development. Configure your preference in the config file:

```php
'frontend' => [
    'framework' => 'livewire', // or 'vue'
],
```

### Livewire Components

```php
use LaravelBuilder\VisualBuilder\Components\Builder;

class YourPage extends Component
{
    public function render()
    {
        return view('your-page', [
            'builder' => new Builder(),
        ]);
    }
}
```

### Vue.js Components

```javascript
import { Builder } from '@laravel-builder/visual-builder';

export default {
    components: {
        Builder,
    },
    // ... component configuration
};
```

## API Documentation

The package automatically generates OpenAPI/Swagger documentation for your APIs. Access it at:

```
/api/documentation
```

## Security

- All generated code follows Laravel security best practices
- Built-in CSRF protection
- XSS prevention
- SQL injection protection
- Rate limiting support

## Contributing

Please see [CONTRIBUTING.md](CONTRIBUTING.md) for details.

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.

## Support

For support, please open an issue in the GitHub repository or contact us at support@laravel-builder.com.

## Credits

- [Laravel Builder Team](https://github.com/laravel-builder)
- [All Contributors](../../contributors) #
