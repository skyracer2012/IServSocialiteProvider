# Iserv

```bash
composer require skyracer2012/IServSocialiteProvider
```

## Installation & Basic Usage

Please see the [Base Installation Guide](https://socialiteproviders.com/usage/), then follow the provider specific instructions below.

### Add configuration to `config/services.php`

```php
'iserv' => [
  'base_uri' => env('ISERV_OID_URL'),
  'client_id' => env('ISERV_OID_CLIENT_ID'),
  'client_secret' => env('ISERV_OID_CLIENT_SECRET'),
  'redirect' => env('ISERV_OID_REDIRECT_URL'),
]
```

### Add provider event listener

Configure the package's listener to listen for `SocialiteWasCalled` events.

Add the event to your `listen[]` array in `app/Providers/EventServiceProvider`. See the [Base Installation Guide](https://socialiteproviders.com/usage/) for detailed instructions.

```php
protected $listen = [
    \SocialiteProviders\Manager\SocialiteWasCalled::class => [
        // ... other providers
        \SocialiteProviders\IServ\IServExtendSocialite::class.'@handle',
    ],
];
```

### Usage

You should now be able to use the provider like you would regularly use Socialite (assuming you have the facade installed):

```php
return Socialite::driver('iserv')->redirect();
```

### Returned User fields

- ``id``
- ``email``
- ``username``
- ``name``