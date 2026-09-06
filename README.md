# Magepack for Magento 2 (SISL fork)

The Magento 2 module that serves the JavaScript bundles produced by
[Magepack](https://github.com/SISL-source/magepack). It adds an admin toggle and
injects the correct bundle on each page type via a layout block.

This is a maintained fork of
[magesuite/magepack-magento](https://github.com/magesuite/magepack-magento),
verified to install and run on **Magento 2.4.9 / PHP 8.4**.

## Why this fork exists

The upstream module's `composer.json` declared **no `require` section at all** —
Composer would install it on any Magento/PHP version without warning, so a shop
could silently pull it onto an incompatible release and only discover the breakage
in production. This fork declares proper `php` and `magento/framework` constraints,
and is tested end-to-end on Magento 2.4.9.

## What changed vs upstream

- Added `require`: `php` 8.1–8.5 and `magento/framework >=103.0.4 <104`
  (Magento 2.4.6–2.4.9), so Composer refuses incompatible installs instead of
  failing silently later.
- Verified on Magento 2.4.9 / PHP 8.4: `setup:upgrade`, `module:enable` and
  bundle serving on category / product / checkout all work with no JS errors.

## Install

```bash
composer require @sisl/magepack-magento
bin/magento module:enable MageSuite_Magepack
bin/magento setup:upgrade
```

Enable at *Stores → Configuration → Advanced → Developer → JavaScript Settings →
Enable JavaScript Bundling with Magepack* after building bundles with the
[Magepack CLI](https://github.com/SISL-source/magepack).

## License

OSL-3.0 — see [LICENSE](LICENSE).

---

Maintained by [SISL](https://sisl.pl) — Magento 2 / Adobe Commerce studio.
