# Security

Unless otherwise mentioned, we follow the [Hardening WordPress Principles](https://codex.wordpress.org/Hardening_WordPress), with the [Plugin Security Guidelines](https://developer.wordpress.org/plugins/security/) and the [Theme Security Guidelines](https://developer.wordpress.org/themes/theme-security/).


For ease of reference, the most important points of the previous standards are described here as well.

## User Capabilities
If your plugin allows users to submit data — be it on the Admin or the Public side — it should check for User Capabilities.

## Data Validation
Data validation is the process of analyzing the data against a predefined pattern (or patterns) with a definitive result: valid or invalid.

Usually this applies to data coming from external sources such as user input and calls to web services via API.

Simple examples of data validation:

- Check that required fields have not been left blank
- Check that an entered phone number only contains numbers and punctuation
- Check that an entered postal code is a valid postal code
- Check that a quantity field is greater than 0

**Data validation should be performed as early as possible. That means validating the data before performing any actions.**

## Securing Inputs
Securing input is the process of sanitizing (cleaning, filtering) input data.

You use sanitizing when you don’t know what to expect or you don’t want to be strict with data validation.

**Any time you’re accepting potentially unsafe data, it is important to validate or sanitize it.**

## Securing Outputs
Securing output is the process of escaping output data.

Escaping means stripping out unwanted data, like malformed HTML or script tags.

**Whenever you’re rendering data, make sure to properly escape it. Escaping output prevents XSS (Cross-site scripting) attacks.**

## Nonces
Nonces are generated numbers used to verify origin and intent of requests for security purposes. Each nonce can only be used once.

If your plugin allows users to submit data; be it on the Admin or the Public side; you have to make sure that the user is who they say they are and that they have the necessary capability to perform the action. Doing both in tandem means that data is only changing when the user *expects* it to be changing.
