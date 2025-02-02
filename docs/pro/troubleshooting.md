<!--
    This source file is part of the open source project
    ExpressionEngine User Guide (https://github.com/ExpressionEngine/ExpressionEngine-User-Guide)

    @link      https://expressionengine.com/
    @copyright Copyright (c) 2003-2021, Packet Tide, LLC (https://packettide.com)
    @license   https://expressionengine.com/license Licensed under Apache License, Version 2.0
-->

# Troubleshooting ExpressionEngine Pro

[TOC=1-3]

## General
### I'm unable to use many Pro features.
If you are unable to use many of Pro features such as front-end editing, Low Search, Low Variables, Cookies management, or other features, then there is most likely an issue with your license. Ensure that your purchased Pro license is attached to a site and double check that your license key in your Site Settings correctly matches the site license key for which your Pro product is attached. For more information on purchasing a license and installing your key, read through the [installation docs](pro/installation.md#purchasing-an-expressionengine-pro-license).

### I do not see included products installed.
If you do not see and wish to use products that are included with ExpressionEngine Pro such as Low Search and Low Variables, then they may not be installed. Please follow the [installation process for included products](pro/installation.md#installation-of-included-products) and ensure that products are installed correctly.

## Front edit links and Dock
### Dock and/or front edit links do not show on the front-end of the website.

There are several settings that could prevent the Dock from showing on the front-end of your site.

- No active session on front-end of site - Users must be logged in to access Pro's features. If any of the following are true, a user could have an active session in to the Control Panel while not having an active session on the front-end if any of the following are true:
    - [Website Session type](control-panel/settings/security-privacy.md#website-session-type) is using "Session ID only" or "Cookies and session ID"
    - [CP Session type](control-panel/settings/security-privacy.md#cp-session-type) is set to "Session ID only"

    If either of these conditions are met, then a user will need to be provided with a [login form](member/login.md) on the front-end of the site so to create an active session on the front-end and access ExpressionEngine Pro features.


- [Role Permissions](pro/permissions.md#expressionengine-pro-role-access) - Users must be assigned a role with proper permissions to use ExpressionEngine Pro on both the front and back-end of the site.

- The Dock is disabled via settings or config override. Disabling the Dock will disable all of Pro's features on the front-end of your site.
    - Via Pro's [general settings](pro/configuration.md#general-settings), ensure that the "Enable Dock?" setting is toggled on.
    - Via the [`enable_dock` config override](pro/configuration.md#enable_dock). If in use, this override must be set to `'y'` for the Dock and Pro features to work on the front-end.

### Dock shows, but front edit links do not show on the front-end of the website.

- Front edit links are disabled via settings or config override.
    - Via Pro's [general settings](pro/configuration.md#general-settings), ensure that the "Enable front-end editing" setting is toggled on.
    - Via the [`enable_frontedit` config override](pro/configuration.md#enable_frontedit). If in use, this override must be set to `'y'` for front-end editing to work.

- User does not have proper access to edit channels. Users must be assigned a role which has access to channels and to be able to edit channel content to see related front edit links on the site.

### Dock shows everywhere, while front edit links only show some places.

- If Front edit links are showing on some templates, but not on others then front edit links may be disabled via template settings. Front-end editing can be enabled/disabled under "Pro Settings" in each template's settings.

![template settings](_images/pro_template_settings.png).

- Automatic front-end editing links are disabled via settings or config override. By default, ExpressionEngine Pro automatically generates front edit links for all entry fields. This can be turned on or off, requiring a developer to [manually insert front edit links](pro/frontend.md#customizing-the-link-location) via template tags. If only manually inserted links are showing, this could be the cause.
    - Via Pro's [general settings](pro/configuration.md#general-settings), ensure that the "Enable automatic front-end editing links" setting is toggled on.
    - Via the [`enable_frontedit_links` config override](pro/configuration.md#enable_frontedit_links). If in use, this override must be set to `'y'` for Pro to automatically insert front edit links.

- Front edit links are disabled via HTML comments, EE template comments, or `disable` parameter. There are 3 ways to disable Pro's automatic generation of front edit links. Ensure that the template code your inspecting isn't surrounded by template comments or wrapped in a field tag using `disable="frontedit`. For details on these methods read the [docs regarding disabling Pro links](pro/frontend.md#disabling-the-front-edit-link) 

- User does not have proper access to edit channels they are viewing. Users must be assigned access to channels and to be able to edit channel content to see related front edit links on the site. If the user is viewing entries on the front-end for which they do not have content, then no front edit links will show.

## License

### ExpressionEngine Pro shows as "unlicensed", "unknown", "invalid key", or "missing key"

- If you have recently made updates to your settings or switch domains in your ExpressionEngine Store licenses, then this may be temporary. A page refresh may resolve the issue in this case.

- Ensure that your purchased Pro license is attached to a site and double check that your license key in your Site Settings correctly matches the site license key for which your Pro product is attached. For more information on purchasing a license and installing your key read through the [installation docs](pro/installation.md#purchasing-an-expressionengine-pro-license).

### A License Error alert shows in the Control Panel

If a license error alert is showing in the Control Panel, such as the one below, then there is an issue with your site license. First ensure that your purchased Pro license is attached to a site and double check that your license key in your Site Settings correctly matches the site license key for which your Pro product is attached. For more information on purchasing a license and installing your key read through the [installation docs](pro/installation.md#purchasing-an-expressionengine-pro-license).

![license error](_images/ee-pro-license-error.png)