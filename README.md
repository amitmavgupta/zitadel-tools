# zitadel-tools

## Installation

```zsh
go install github.com/zitadel/zitadel-tools@latest
```

## key2jwt 

Convert a *key file* to *jwt token*

### Usage

key2jwt requires two flags:

- audience: where the assertion is going to be used (e.g. https://zitadel.cloud or https://{your domain})
- key: the path to the key.json

The tool prints the result to standard output.

```zsh
zitadel-tools key2jwt --audience=https://zitadel.cloud --key=key.json
```

Optionally you can pass an `output` flag. This will save the jwt in the provided file path:

```zsh
zitadel-tools key2jwt --audience=https://zitadel.cloud --key=key.json --output=jwt.txt
```

You can also create a JWT by providing a RSA private key (.pem file). You then also need to specify the issuer of the token:
```zsh
zitadel-tools key2jwt --audience=https://zitadel.cloud --key=key.pem --issuer=client_id
```

## basicauth

Convert *client ID* and *client secret* to be used in *Authorization* header for [Client Secret Basic](https://zitadel.com/docs/apis/openidoauth/authn-methods#client-secret-basic)

### Usage

basicauth requires two flags:

- id: client id
- secret: client secret

The tool prints the URL- and Base64 encoded result to standard output

```zsh
zitadel-tools basicauth --id $CLIENT_ID --secret $CLIENT_SECRET
```

## Migrate data to ZITADEL import

Zitadel-tools can be used to transform exported data from other providers
to the import schema of Zitadel. We currently support [Auth0](cmd/migration/auth0/readme.md) and [Keycloak](cmd/migration/keycloak/readme.md).

To print available sub-commands and flags:

```zsh
zitadel-tools migrate --help
```
