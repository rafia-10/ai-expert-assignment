# Explanation

## What was the bug?

When `Client.oauth2_token` was set as a dictionary, API requests did not attach an `Authorization` header and did not trigger a token refresh. This caused unauthenticated requests.

## Why did it happen?

The `request()` method only handled `OAuth2Token` instances when checking expiration and adding headers. Dictionary tokens were ignored, even though the type annotation explicitly allowed them (`Union[OAuth2Token, Dict[str, Any], None]`).

## Why does your fix actually solve it?

The fix normalizes dictionary tokens into `OAuth2Token` instances before expiration checks. This ensures the token refresh logic and header injection work consistently for both `dict` and `OAuth2Token`.

## One realistic edge case / not covered in tests

A dictionary missing required keys (`access_token` or `expires_at`) would raise a `TypeError` during normalization. This case is not currently tested.
