<!--
    This source file is part of the open source project
    ExpressionEngine User Guide (https://github.com/ExpressionEngine/ExpressionEngine-User-Guide)

    @link      https://expressionengine.com/
    @copyright Copyright (c) 2003-2020, Packet Tide, LLC (https://packettide.com)
    @license   https://expressionengine.com/license Licensed under Apache License, Version 2.0
-->

# Resetting a Forgotten Password

[TOC]

## Overview

Logged out users can have a password reset link emailed to their account email, and using that link, securely reset their password without knowing their current password.  There are two steps to resetting a forgotten password.

In the first step, an email address associated with a member account must be submitted.  Instructions for resetting the password will be sent to that address.

In the second step, the user follows the link in the email to the forgotten password form, where they set a new password.

NOTE: **Note:** Logged in users wanting to change their password should use the [Edit Profile Tag](member/edit-profile.md).

## Forgotten Password Email Form

Output a forgotten password form that sends an email with instructions for resetting a member password when unable to login.

    {exp:member:forgot_password_form}

            <label>Your Email Address</label><br />
            <input type="email" name="email" value="" maxlength="120" size="40" />

			<input type="submit" name="submit" value="Submit" />

    {/exp:member:forgot_password_form}

### Parameters

#### `password_reset_email_template=`

    password_reset_email_template="member/email-password-reset"

#### `password_reset_url=`

    password_reset_url="member/reset-password"

#### `return=`

    return="member/forgot-password/sent"


### Form Inputs

#### Email

Member email address. This is a **required** field:

    <label for="email">Email</label>
    <input type="email" name="email" value="" maxlength="120" size="40" />


### Variable Pairs

#### `{errors}`

Form submission errors are displayed using a "looping pair" as there can be more than 1 error in a form submission.

    {errors}
        <p>{error}</p>
    {/errors}

#### Error Tag Pair Parameters

##### `backspace=`

    backspace="3"

The `backspace=` parameter will remove characters, including spaces and line breaks, from the last iteration of the tag pair.

#### Error Tag Pair Variables

##### `{error}`

    {error}

The error text.


### Example

    {exp:member:forgot_password_form
        return="member/forgot-password/sent"
        password_reset_url="member/reset-password"
        password_reset_email_template="member/email-password-reset"
        }

        <p>
            <label>Your Email Address</label><br />
            <input type="email" name="email" value="" maxlength="120" size="40" />
        </p>

        <p><input type="submit" name="submit" value="Submit" /></p>

        <p><a href="{path='member/login'}">Login</a> &nbsp; &nbsp; <a href="{path='member/registration'}">Register</a></p>
    {/exp:member:forgot_password_form}

## Forgotten Password Reset Password Form

Output a reset password form that allows members accessing it via a link from a forgotten email form to reset their password while logged out.

    {exp:member:reset_password_form}

            <label>Your Email Address</label><br />
            <input type="email" name="email" value="" maxlength="120" size="40" />

			<input type="submit" name="submit" value="Submit" />

    {/exp:member:reset_password_form}
### Parameters

#### `return=`

    return="member/login/success"


### Form Inputs

#### Password

            <label>Your New Password</label><br />
            <input type="password" name="password" value="" maxlength="50" size="40" />

The new password to set.

#### Password Confirmation

            <label>Confirm New Password</label><br />
            <input type="password" name="password_confirm" value="" maxlength="50" size="40" />


Duplicate of the new password set in the password form input.


### Variable Pairs

#### `{errors}`

Form submission errors are displayed using a "looping pair" as there can be more than 1 error in a form submission.

    {errors}
        <p>{error}</p>
    {/errors}

#### Error Tag Pair Parameters

##### `backspace=`

    backspace="3"

The `backspace=` parameter will remove characters, including spaces and line breaks, from the last iteration of the tag pair.

#### Error Tag Pair Variables

##### `{error}`

    {error}

The error text.

### Example

    {exp:member:reset_password_form
        return="member/login/success"
        }

        <p>
            <label>Your New Password</label><br />
            <input type="password" name="password" value="" maxlength="50" size="40" />
        </p>

        <p>
            <label>Confirm New Password</label><br />
            <input type="password" name="password_confirm" value="" maxlength="50" size="40" />
        </p>

        <p><input type="submit" name="submit" value="Submit" /></p>

        <p><a href="{path='member/login'}">Login</a> &nbsp; &nbsp; <a href="{path='member/registration'}">Register</a></p>
    {/exp:member:reset_password_form}
