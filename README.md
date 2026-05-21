# BOSS OAuth client metadata

Public OAuth client metadata documents for the BOSS automation team's
integrations with OAuth-enabled services (Lovable MCP, etc.).

These files implement RFC 7591 client metadata documents that can be
referenced by URL as an OAuth `client_id` per the SEP-991 / "URL-based
Client IDs" pattern. Used when an authorization server supports
`client_id_metadata_document_supported: true` but disables dynamic
registration.

## Contents

- `lovable.json` — Client metadata for the BOSS Lovable Builder dispatcher
  (`C:\BusinessOS\tools\lovable-builder.js`). Used as the `client_id` value
  when initiating an OAuth Authorization Code + PKCE flow against
  `https://lovable.dev/oauth/authorize`.

## Security note

These documents contain **no secrets**. They declare what redirect URIs
the client is allowed to use and what scopes it requests. The actual
authentication still requires a successful OAuth authorization code flow
with the resource owner's credentials. Anyone can read these files;
nobody can use them to impersonate the client without also completing
the full PKCE flow against a logged-in Lovable session.
