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
- Data validation should be performed as early as possible. That means validating the data before performing any actions.
