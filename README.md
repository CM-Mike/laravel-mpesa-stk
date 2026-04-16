# Laravel M-Pesa STK Push

[![Latest Version on Packagist](https://img.shields.io/packagist/v/cm-mike/laravel-mpesa-stk.svg?style=flat-square)](https://packagist.org/packages/cm-mike/laravel-mpesa-stk)
[![Total Downloads](https://img.shields.io/packagist/dt/cm-mike/laravel-mpesa-stk.svg?style=flat-square)](https://packagist.org/packages/cm-mike/laravel-mpesa-stk)
[![License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE.md)

A streamlined, developer-friendly Laravel package for integrating Safaricom's Daraja API STK Push (Lipa na M-Pesa Online). Built for speed, security, and ease of use in the Kenyan fintech ecosystem.

---

## 🚀 Features

- **Auto-Discovery:** Zero-config installation for Laravel 10.x and 11.x.
- **Facade Support:** Clean, expressive syntax using the `Mpesa` facade.
- **Environment Aware:** Seamless switching between `sandbox` and `production` environments.
- **Guzzle Powered:** Robust HTTP requests with built-in error handling.
- **Secure:** Configuration driven by `.env` to keep your credentials safe.

## 📦 Installation

Install the package via composer:

```bash
composer require cm-mike/laravel-mpesa-stk
````

The package will automatically register itself using Laravel's auto-discovery.

### Publish Configuration

Publish the config file to your application's config directory:

```bash
php artisan vendor:publish --tag="mpesa-config"
```

## ⚙️ Configuration

Add the following variables to your `.env` file:

```env
MPESA_ENV=sandbox # use 'production' for live apps
MPESA_SHORTCODE=174379
MPESA_PASSKEY=your_daraja_passkey
MPESA_CONSUMER_KEY=your_consumer_key
MPESA_CONSUMER_SECRET=your_consumer_secret
MPESA_CALLBACK_URL=[https://your-domain.com/api/mpesa/callback](https://your-domain.com/api/mpesa/callback)
```

## 🛠 Usage

### Initiating an STK Push

You can use the `Mpesa` facade to trigger a payment request to a user's phone:

```php
use CMMike\MpesaStk\Facades\Mpesa;
use Illuminate\Support\Facades\Log;

try {
    $response = Mpesa::initiate(
        100,                  // Amount in KES
        '2547XXXXXXXX',       // Customer Phone Number
        'INV-001',            // Account Reference
        'Payment for Goods'   // Transaction Description
    );

    if ($response->ResponseCode == '0') {
        // Success: STK Push sent to phone
        return response()->json(['message' => 'Check your phone to complete payment']);
    }
} catch (\Exception $e) {
    // Handle errors (e.g., connection issues)
    Log::error("M-Pesa Error: " . $e->getMessage());
}
```

## 🧪 Testing

```bash
composer test
```

## 🤝 Contributing

Contributions are welcome. Please feel free to fork the repository and submit a pull request.

## 🛡️ Security

If you discover any security-related issues, please email **awirotieno@gmail.com** instead of using the issue tracker.

## 📜 Credits

  - [Churchill Mikes](https://github.com/CM-Mike)
  - [All Contributors](https://www.google.com/search?q=../../contributors)

## 📄 License

The MIT License (MIT). Please see [License File](https://www.google.com/search?q=LICENSE.md) for more information.

```
```
