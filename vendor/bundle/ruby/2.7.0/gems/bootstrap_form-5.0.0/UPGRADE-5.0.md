# Upgrading to `bootstrap_form` 5.0

We made every effort to make the upgrade from `bootstrap_form` v4 (Bootstrap 4) to `bootstrap_form` 5.0 (Bootstrap 5) as easy as possible. However, Bootstrap 5 is fundamentally different from Bootstrap 4, so some changes may be necessary in your code.

## Bootstrap 5 Changes

Upgrading `bootstrap_form` to version 5 means you must upgrade your whole application to Bootstrap 5. Read the [Bootstrap 5 migration guide](https://v5.getbootstrap.com/docs/5.0/migration/) to see what changes you have to make to your views. This will also help you understand changes you might have to make to your `bootstrap_form` code.

## `bootstrap_form` Version 5 Changes

## No `role="form"` Attribute

As explained in #560, the `role="form"` attribute generated by `bootstrap_4` caused the W3C validator to output a warning. The `role="form"` attribute was deprecated in the 4.5.0 and is being remove completely in 5.0.0. This has no impact on `bootstrap_form` code itself, but may affect your application if it depended on a form having this attribute set. (Issue #569)

## Different behavior for `errors_on` helper

The `errors_on` helper now wraps the error message in a CSS class `invalid-feedback`, instead of `alert` and `alert-danger`, as before.

This will display the error as any other [Bootstrap inline form error](https://getbootstrap.com/docs/5.0/forms/validation/#server-side), instead of displaying it as an [Bootstrap alert](https://getbootstrap.com/docs/5.0/components/alerts/).

You can use the `custom_class` options for this helper with `alert alert-danger` to restore the old behaviour:

```erb
<%= f.errors_on :tasks, custom_class: 'alert alert-danger' %>
```
