# Simple Cookie Creator
A lightweight and performant **Google Tag Manager (Web)** template to create browser cookies with configurable attributes such as expiration, SameSite, Secure, and domain handling.

The template is designed as a utility helper for advanced GTM setups (e.g. server-side tracking, consent-aware workflows, identifier persistence).

## Features

- Create **persistent cookies** with configurable expiration (days / hours / minutes)
- Create **session cookies** (no expiration set)
- Configure common cookie attributes:
  - `domain`
  - `path`
  - `secure`
  - `SameSite`
- Optional **skipUndefined** logic to prevent writing cookies with empty or undefined values
- Works with **server-side or client-side logic** that determines cookie values
- No third-party dependencies

## Use cases

Typical scenarios include:

- Writing first-party utility cookies
- Persisting non-PII state (e.g. feature flags, experiment buckets)
- Bridging data between client-side logic and server-side GTM
- Controlled cookie creation in consent-aware setups

> ⚠️ This template **does not manage consent**. It assumes consent decisions are handled upstream (e.g. CMP, Consent Mode, or custom logic).

## Template type

- **Container**: Web
- **Category**: Utilities
- **Execution**: Client-side

## Configuration

### Required fields

| Field | Description |
|------|-------------|
| Cookie Name | Name of the cookie to set |
| Cookie Value | Value to write into the cookie |
| Expiration Mode | `days`, `hours`, `minutes`, or `session` |
| Expiration Value | Numeric value used with the selected mode |

### Optional fields

| Field | Description |
|------|-------------|
| Domain | Cookie domain (default: `auto`) |
| Path | Cookie path (default: `/`) |
| Secure | Whether to set the `Secure` flag |
| SameSite | `lax`, `strict`, or `none` |
| Skip undefined values | Prevents writing cookies if the value is `undefined`, `null`, or empty |

## Behavior notes

- **Session mode** does not set `max-age` or `expires`
- When **skipUndefined** is enabled and the value is empty or undefined:
  - No cookie is written
  - The tag exits successfully
- All logic is synchronous and deterministic

## Permissions

This template requests only the permissions required for its functionality:

- `set_cookies` – required to write browser cookies
- `logging` – used for optional debug output

## Testing

The template includes automated tests covering:

- Standard persistent cookie creation
- Session cookie behavior (no expiration set)
- Skip-undefined logic preventing cookie writes

Tests are executed using GTM’s built-in template test framework.

## Installation

### From the Community Template Gallery
1. Open Google Tag Manager
2. Go to **Templates → Search Gallery**
3. Search for **Simple Cookie Creator**
4. Add the template to your container

### From source
1. Download `template.tpl`
2. Import it via **Templates → New → Import**

## License

This project is licensed under the **Apache License 2.0**.  
See the `LICENSE` file for details.

## Author / Maintainer

**Norman Höhne**

- GitHub: https://github.com/NormanHoehne

Issues and improvement suggestions are welcome via GitHub Issues.
