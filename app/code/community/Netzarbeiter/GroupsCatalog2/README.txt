/**
 * Netzarbeiter
 *
 * NOTICE OF LICENSE
 *
 * This source file is subject to the Open Software License (OSL 3.0)
 * that is bundled with this package in the file LICENSE.txt.
 * It is also available through the world-wide-web at this URL:
 * http://opensource.org/licenses/osl-3.0.php
 *
 * DISCLAIMER
 *
 * Do not edit or add to this file if you wish to upgrade this Module to
 * newer versions in the future.
 *
 * @category   Netzarbeiter
 * @package    Netzarbeiter_GroupsCatalog2
 * @copyright  Copyright (c) 2011 Vinai Kopp http://netzarbeiter.com
 * @license    http://opensource.org/licenses/osl-3.0.php  Open Software License (OSL 3.0)
 */

== ABOUT ==

This extension enables you to hide categories and products from customers depending on their customer
group. It is a rewrite of the Magento extension Netzarbeiter_GroupsCatalog for Magento 1.6 and newer.

If you use Magento 1.5 or 1.4 please refer to the older extension which is linked
to from this modules page on Magento Connect.

This rewrite not only cleans up the code base, it also adds several new features and improvements:
- Configurable if you want to hide everything and select products and categories to show or vica versa.
- Use of an index which means support of an unlimited customer groups without DB table hacks.
- Faster frontend usage, especially noticeable with large catalogs and complex settings.
- Fully configurable on a store view level.


== USAGE ==

You can specify a default visibility setting for all categories and products under
System / Configuration / Netzarbeiter Extensions / Groups Catalog 2

There you can also choose to disable the extension (on a store view level).

The default after installation is no categories or products are hidden.
You can override the default settings for every product and category in the Product
Management and Category Management pages.

If you use some non-standard mechanism or import for products and categories, it might be necessary to
rebuild the GroupsCatalog index. You can do so by visiting the Page System / Index Management.
There check the checkboxes beside the indexes "GroupsCatalog Products" and "GroupsCatalog Categories", select the
"Reindex Data" action and click the "Submit" button.


== INSTALL ==

After installation please refresh the cache, and then log out of the admin area and log back in again
to avoid getting a 404 error on the Module configuration page.
Then visit the configuration page at
System / Configuration / Netzarbeiter Extensions / Groups Catalog 2
and configure as needed.

== UPGRADE from 1.5 ==

I'm planning to add a migration script to move configuration settings from the old version of the
extension to the new one. But currently there is no such thing yet.

== UNINSTALL ==

If you ever uninstall the extension (I don't hope so ;)) your site will be broken, because
Magento does not support a mechanism to automatically execute a script when an extension is
removed. This script adds two attributes with custom source, frontend and backend models,
and when the extension is removed Magento can't find those models anymore.
To fix the Error, you have to execute the following SQL:

    DELETE FROM `eav_attribute` WHERE attribute_code = 'groupscatalog2_groups';
    DELETE FROM `core_resource` WHERE code = 'netzarbeiter_groupscatalog2_setup';

Don't forget to clear the cache, afterwards.


== CHANGES ==

0.1.0 - Initial release of the GroupsCatalog2 module


== KNOWN ISSUES ==

Currently, none.
If you find any please write me an email to "vinai (you know what) netzarbeiter [the little round thing] com"
with Netzarbeiter_GroupsCatalog2 as part of the subject. Thanks.

== CONTACT ==

Please write me an email with ideas or bugreports to "vinai (you know what) netzarbeiter [the little round thing] com"
with Netzarbeiter_GroupsCatalog2 as part of the subject.